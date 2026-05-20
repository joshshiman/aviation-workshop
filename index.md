---
layout: default
title: Home
---

# ✈️ Aviation Workshop

Build a real-time aviation warning system using **Kafka**, **watsonx Orchestrate**, and **AI agents**.

## 🎯 Workshop Overview

In this hands-on workshop, you'll build an intelligent aviation safety system that:
- **Streams real-time data** from Kafka (weather events and flight telemetry)
- **Analyzes conditions** using AI agents powered by watsonx Orchestrate
- **Generates alerts** when flights approach hazardous weather
- **Visualizes everything** on an interactive dashboard

## 📚 Labs

### [Lab 1: Environment Setup](docs/lab-1-setup/)
**Duration:** 30 minutes

Set up your development environment and obtain API credentials:
- Get workshop materials from Box
- Join IBM Cloud and get watsonx Orchestrate credentials
- Configure Python environment
- Test your connections

### [Lab 2: Kafka Consumer](docs/lab-2-kafka/)
**Duration:** 30-45 minutes

Build a Kafka consumer to process real-time flight and weather events:
- Create a Kafka consumer using prebuilt helpers
- Process weather and flight events
- Understand the event flow
- Print and inspect data structures

### [Lab 3: Building AI Agents](docs/lab-3-agents/)
**Duration:** 60 minutes

Create intelligent agents that analyze weather conditions and assess flight risks:
- Build a Weather Analysis Tool using watsonx Orchestrate
- Build a Flight Risk Assessment Tool
- Test your tools locally
- Deploy tools to watsonx Orchestrate

### [Lab 4: Interactive Dashboard](docs/lab-4-dashboard/)
**Duration:** 45 minutes

Build a real-time web dashboard to visualize the system:
- Create a real-time dashboard using vanilla JavaScript
- Integrate Leaflet maps for geospatial visualization
- Display flight positions and weather hazards
- Show AI-generated alerts in real-time

## 🛠️ Technologies Used

- **Apache Kafka** - Real-time data streaming
- **watsonx Orchestrate** - AI agent orchestration
- **Python 3.11** - Backend development
- **Flask** - API server
- **Leaflet.js** - Interactive maps
- **IBM Carbon Design System** - UI styling

## 📋 Prerequisites

- Basic Python knowledge
- Familiarity with REST APIs
- Understanding of JSON data structures
- A laptop with internet connection

## 🚀 Getting Started

1. Clone this repository
2. Follow [Lab 1: Environment Setup](docs/lab-1-setup/) to configure your environment
3. Work through each lab sequentially
4. Ask questions and experiment!

## 📖 Additional Resources

- [watsonx Orchestrate Documentation](https://www.ibm.com/docs/en/watsonx/watson-orchestrate)
- [Apache Kafka Documentation](https://kafka.apache.org/documentation/)
- [Leaflet.js Documentation](https://leafletjs.com/)
- [IBM Carbon Design System](https://carbondesignsystem.com/)

## 🤝 Support

If you encounter issues during the workshop:
- Check the troubleshooting section in each lab
- Ask your instructor for help
- Review the example files in the repository

---

**Ready to begin?** Start with [Lab 1: Environment Setup](docs/lab-1-setup/) →