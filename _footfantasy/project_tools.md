---
title: "Project Tools"
excerpt: "Project tools"
last_modified_at: 2023-01-11 10:22:00 +0100
toc: true
---
<script src="/assets/js/mermaid.min.js"></script>

## Development
VSCode

## Alerting
Watcher with elastic search

## Monitoring
### Flow Chart
<div class="mermaid">
graph LR
    kafka>Kafka] --> logstash(Logstash)
    data_source>Data Source] --> logstash
    logstash --> elasticsearch[(Elasticsearch)]
    kibana(Kibana) --> elasticsearch
</div>

### Kafka

### Kibana
Visualization tool

### Elasticsearch
Data Storage

### Logstash
Graphana ?
StatsD ?
