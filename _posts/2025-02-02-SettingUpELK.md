---
title: Setting up the ELK Stack with Docker for Local Testing
date: 2025-02-02
categories: [ELK]
tags: [ELK stack, docker, log analysis, elasticsearch, kibana, logstash, metricbeat, filebeat, APM, fleet, observability, security]
author: harmehar kaur
image:
  path: /assets/forensics.jpg
  alt: 
---

I recently found myself struggling to get the full ELK stack running on my student laptop — it's just not built for heavy lifting like this. Luckily, I stumbled across a fantastic two-part blog series on Elastic’s official site, which walks through how to set everything up using Docker. Instead of splitting it, I’ve condensed the process into one post here and added my notes. The full source files, configs, and app examples are available on GitHub:  
👉 **[Elastic’s GitHub Repository](https://github.com/elkninja/elastic-stack-docker-part-two)**

---

## 🚀 Why Docker for ELK?

The Elastic Stack (Elasticsearch, Logstash, Kibana, Beats, APM, etc.) is incredibly powerful, but also pretty complex to set up manually. Docker makes it easier to spin everything up for local development or proof-of-concept (POC) environments without sacrificing too much time or sanity.

---

## 📁 File Structure

Here’s the basic structure:

```
├── .env
├── docker-compose.yml
├── kibana.yml
├── metricbeat.yml
├── filebeat.yml
├── logstash.conf
├── app/
│   ├── Dockerfile
│   ├── main.py
│   └── requirements.txt
```

---

## ⚙️ The `.env` File

The `.env` file helps manage environment variables like ports, memory limits, and passwords. It's also where you set the version of the Elastic Stack and other important configs like APM secret tokens and encryption keys.

A few key things:
- Use secure passwords and tokens.
- Set your `STACK_VERSION`, e.g., `8.7.1`.
- Ports like `9200` for Elasticsearch, `5601` for Kibana, `8200` for APM, and `8220` for Fleet should be exposed.

---

## 🐳 Docker Compose Configuration

The `docker-compose.yml` file sets up services for:
- **Elasticsearch** (core database and search engine)
- **Kibana** (dashboard/UI)
- **Logstash** (data processing)
- **Metricbeat** (system metrics)
- **Filebeat** (log ingestion)
- **Fleet Server & Elastic Agent** (centralized management)
- **APM** (performance monitoring)
- **Sample Python Web App** (for testing APM)

It handles cert generation, mounts volumes for persistence, and defines health checks to ensure all services start in the correct order.

---

## 🔐 Certificate Setup

Elastic now enforces security by default (as it should!). So part of the process involves spinning up a `setup` container that generates SSL certificates for all services. These certs ensure secure communication between containers and your browser.

---

## 🧪 Testing the Stack

After everything is up with `docker-compose up`, you can:
- Access **Kibana** at `https://localhost:5601`
- Test **Elasticsearch** with:
  ```bash
  curl --cacert /tmp/ca.crt -u elastic:changeme https://localhost:9200
  ```

---

## 📊 Observability: Metricbeat + Filebeat

These Beats help feed system and log data into Elasticsearch.

- **Metricbeat**: Monitors containers, system metrics, and services like Elasticsearch, Logstash, Kibana.
- **Filebeat**: Captures log files and container logs. Great for testing custom logs — just drop a `.log` file in the mounted ingest folder.

---

## 🔄 Data Pipeline: Logstash

Logstash reads files from a shared folder and pushes parsed output into Elasticsearch under the `logstash-*` index. Customize `logstash.conf` to suit your use case.

---

## 🌐 Elastic Agent, Fleet, APM & Custom App

- **Fleet**: Central hub in Kibana to manage agents.
- **Elastic Agent**: Collects logs, metrics, and runs integrations.
- **APM**: Performance insights on your app — we use a sample Python app with FastAPI and NiceGUI.
- **Fleet Server**: Handles coordination between agents and Kibana.

> Make sure to adjust the **Fleet output settings in Kibana UI** to point to `https://es01:9200`, and paste in your CA cert and fingerprint.

---

## 🧠 Monitoring & Visualization

Once everything is connected:
- Head to **Kibana > Observability > APM** to see performance metrics.
- Check **Fleet > Agents** to see your monitored hosts.
- Use **Stack Monitoring** for a real-time view of your entire ELK setup.

---

## 💡 Final Thoughts

This Docker-based setup is perfect for local learning, experimenting with integrations, or building POCs without spinning up full cloud infrastructure. Just remember:

- Don't use this exact setup in production.
- Update all default credentials.
- Always use HTTPS and proper certificate management.

🔗 **Original Guide and GitHub Source**:  
[Elastic’s Docker ELK Guide](https://www.elastic.co/blog/getting-started-with-the-elastic-stack-and-docker-compose)

---

Let me know if you want a simplified version with just the essentials, or a visual walkthrough using screenshots and architecture diagrams. Happy stacking! 📦
