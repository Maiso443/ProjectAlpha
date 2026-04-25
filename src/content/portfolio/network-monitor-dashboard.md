---
title: 'Network Monitor Dashboard'
description: 'Self-hosted dashboard for tracking uptime and latency across home lab devices.'
pubDate: 'Mar 15 2026'
heroImage: '../../assets/blog-placeholder-1.jpg'
tags: ['homelab', 'monitoring']
link: 'https://github.com/Maiso443/network-monitor'
status: 'active'
---

A small Grafana + Prometheus setup I run at home to keep an eye on the network.

It currently tracks ping, throughput, and DNS resolution times across a dozen
devices. The whole stack runs in a single Docker Compose file on a Raspberry Pi
4, with alerts pushed to a private Telegram channel when anything stays down
for more than 60 seconds.
