<!--startmeta
custom_edit_url: "https://github.com/netdata/netdata/edit/master/src/collectors/windows.plugin/integrations/network_subsystem.md"
meta_yaml: "https://github.com/netdata/netdata/edit/master/src/collectors/windows.plugin/metadata.yaml"
sidebar_label: "Network Subsystem"
learn_status: "Published"
learn_rel_path: "Collecting Metrics/Windows Systems"
most_popular: False
message: "DO NOT EDIT THIS FILE DIRECTLY, IT IS GENERATED BY THE COLLECTOR'S metadata.yaml FILE"
endmeta-->

# Network Subsystem


<img src="https://netdata.cloud/img/windows.svg" width="150"/>


Plugin: windows.plugin
Module: PerflibNetwork

<img src="https://img.shields.io/badge/maintained%20by-Netdata-%2300ab44" />

## Overview

Monitor network interface metrics about bandwidth, state, errors and more.


It queries 'Network Interface' and 'Network Adapter' objects from Perflib in order to gather the metrics.


This collector is only supported on the following platforms:

- windows

This collector only supports collecting metrics from a single instance of this integration.


### Default Behavior

#### Auto-Detection

The collector automatically detects all of the metrics, no further configuration is required.


#### Limits

The default configuration for this integration does not impose any limits on data collection.

#### Performance Impact

The default configuration for this integration is not expected to impose a significant performance impact on the system.


## Metrics

Metrics grouped by *scope*.

The scope defines the instance that the metric belongs to. An instance is uniquely identified by a set of labels.



### Per System

These metrics refer to the entire System.

This scope has no labels.

Metrics:

| Metric | Dimensions | Unit |
|:------|:----------|:----|
| system.net | received, sent | kilobits/s |
| ip.tcppackets | received, sent | packets/s |
| ipv4.packets | received, sent, forwarded, delivered | packets/s |
| ipv4.tcppackets | received, sent | packets/s |
| ipv4.udppackets | received, sent | packets/s |
| ipv4.icmp | received, sent | packets/s |
| ipv4.errors | InDiscards, OutDiscards, OutNoRoutes, InAddrErrors, InHdrErrors, InUnknownProtos | packets/s |
| ipv4.icmpmsg | InEchoReps, OutEchoReps, InDestUnreachs, OutDestUnreachs, InRedirects, OutRedirects, InEchos, OutEchos, InRouterAdvert, OutRouterAdvert, InRouterSelect, OutRouterSelect, InTimeExcds, OutTimeExcds, InParmProbs, OutParmProbs, InTimestamps, OutTimestamps, InTimestampReps, OutTimestampReps | packets/s |
| ipv6.packets | received, sent, forwarded, delivered | packets/s |
| ipv6.tcppackets | received, sent | packets/s |
| ipv6.udppackets | received, sent | packets/s |
| ipv6.icmp | received, sent | packets/s |
| ipv6.errors | InDiscards, OutDiscards, OutNoRoutes, InAddrErrors, InHdrErrors, InUnknownProtos | packets/s |
| ipv6.icmpmsg | InEchoReps, OutEchoReps, InDestUnreachs, OutDestUnreachs, InRedirects, OutRedirects, InEchos, OutEchos, InRouterAdvert, OutRouterAdvert, InRouterSelect, OutRouterSelect, InTimeExcds, OutTimeExcds, InParmProbs, OutParmProbs, InTimestamps, OutTimestamps, InTimestampReps, OutTimestampReps | packets/s |

### Per network device

These metrics refer to Network Interfaces.

Labels:

| Label      | Description     |
|:-----------|:----------------|
| interface_type | Classification of the network interface (real or virtual). |
| device | System-assigned network interface identifier. |

Metrics:

| Metric | Dimensions | Unit |
|:------|:----------|:----|
| net.net | received, sent | kilobits/s |
| net.packets | received, sent | packets/s |
| net.speed | speed | kilobits/s |
| net.errors | inbound, outbound | errors/s |
| net.drops | inbound, outbound | drops/s |
| net.queue_length | length | packets |
| net.rsc_connections | connections | connections |
| net.rsc_packets | packets | packets/s |
| net.rsc_exceptions | exceptions | exceptions/s |
| net.rsc_average_packet_size | average | bytes |
| net.chimney_connections | connections | connections |



## Alerts


The following alerts are available:

| Alert name  | On metric | Description |
|:------------|:----------|:------------|
| [ inbound_packets_dropped_ratio ](https://github.com/netdata/netdata/blob/master/src/health/health.d/net.conf) | net.drops | Ratio of inbound dropped packets for the network interface ${label:device} over the last 10 minutes |
| [ outbound_packets_dropped_ratio ](https://github.com/netdata/netdata/blob/master/src/health/health.d/net.conf) | net.drops | Ratio of outbound dropped packets for the network interface ${label:device} over the last 10 minutes |
| [ 1m_received_traffic_overflow ](https://github.com/netdata/netdata/blob/master/src/health/health.d/net.conf) | net.net | Average inbound utilization for the network interface ${label:device} over the last minute |
| [ 1m_sent_traffic_overflow ](https://github.com/netdata/netdata/blob/master/src/health/health.d/net.conf) | net.net | Average outbound utilization for the network interface ${label:device} over the last minute |
| [ network_interface_output_queue_length ](https://github.com/netdata/netdata/blob/master/src/health/health.d/net.conf) | net.queue_length | Output Queue Length on interface ${label:device} should be zero, otherwise there are delays and bottlenecks. |


## Setup

### Prerequisites

No action required.

### Configuration

#### File

The configuration file name for this integration is `netdata.conf`.
Configuration for this specific integration is located in the `[plugin:windows]` section within that file.

The file format is a modified INI syntax. The general structure is:

```ini
[section1]
    option1 = some value
    option2 = some other value

[section2]
    option3 = some third value
```
You can edit the configuration file using the [`edit-config`](https://github.com/netdata/netdata/blob/master/docs/netdata-agent/configuration/README.md#edit-a-configuration-file-using-edit-config) script from the
Netdata [config directory](https://github.com/netdata/netdata/blob/master/docs/netdata-agent/configuration/README.md#the-netdata-config-directory).

```bash
cd /etc/netdata 2>/dev/null || cd /opt/netdata/etc/netdata
sudo ./edit-config netdata.conf
```
#### Options



| Name | Description | Default | Required |
|:----|:-----------|:-------|:--------:|
| PerflibNetwork | An option to enable or disable the data collection. | yes | no |

#### Examples
There are no configuration examples.

