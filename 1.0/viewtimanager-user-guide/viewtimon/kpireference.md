---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: KPI_Reference
id: KWS-CP2E-E29-FCN
slug: kpireference
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 18:25:41'
---
# **<span align="center">Network Traffic Analyzer KPI Reference Guide</span>**

<br />

<span align="justify">This document provides a comprehensive description of all Key Performance Indicators (KPIs) extracted by the probe analyzer from live Ethernet traffic. The system inspects packets at every layer of the protocol stack from Ethernet framing through application-layer protocols and computes a rich set of metrics for network monitoring, quality assurance, and troubleshooting.</span>

<span align="justify">KPIs are organized by protocol section. Each section lists every metric extracted for that protocol, its reported field name, data type, unit, and a description of what it measures and how it is computed.</span>

---

## Table of Contents

1.  [Common / IP Layer KPIs](#1-common--ip-layer-kpis)
2.  [TCP](#2-tcp)
3.  [UDP](#3-udp)
4.  [HTTP](#4-http)
5.  [TLS / HTTPS](#5-tls--https)
6.  [DNS](#6-dns)
7.  [SIP (VoIP Signaling)](#7-sip-voip-signaling)
8.  [RTP / RTCP (VoIP Media)](#8-rtp--rtcp-voip-media)
9.  [ICMP](#9-icmp)
10.  [ICMPv6](#10-icmpv6)
11.  [DHCP](#11-dhcp)
12.  [DHCPv6](#12-dhcpv6)
13.  [TWAMP](#13-twamp)
14.  [FTP](#14-ftp)
15.  [GRE](#15-gre)
16.  [Application Layer (DPI)](#16-application-layer-dpi)
17.  [Other L4 Protocols](#17-other-l4-protocols)

---

## **1\. Common / IP Layer KPIs**

These KPIs are extracted at the Ethernet, VLAN, IPv4, and IPv6 inspection layers. They provide the foundational network identification and traffic volume metrics that are attached to every reported flow regardless of the upper-layer protocol.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>timestamp</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the last packet observed in the flow (epoch microseconds).</p></td></tr><tr><td><p><code>first_timestamp</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the first packet observed in the flow.</p></td></tr><tr><td><p><code>vlan_id</code></p></td><td><p>uint32</p></td><td><p>—</p></td><td><p>IEEE 802.1Q VLAN tag identifier extracted from the Ethernet frame. Supports stacked (QinQ) VLAN tags; the innermost VLAN ID is reported.</p></td></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Source IP address (client / uplink side) in dotted-decimal (IPv4) or colon-hex (IPv6) notation. Direction is determined by server pool configuration, SYN flag analysis, or port-number heuristics.</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Destination IP address (server / downlink side).</p></td></tr><tr><td><p><code>net_src_ipv6</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Explicit IPv6 source address field, reported when the flow is IPv6.</p></td></tr><tr><td><p><code>net_dst_ipv6</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Explicit IPv6 destination address field.</p></td></tr><tr><td><p><code>net_ipv6_over_ipv4</code></p></td><td><p>bool</p></td><td><p>—</p></td><td><p>Flag indicating the flow is an IPv6 packet encapsulated inside an IPv4 tunnel (protocol 41).</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Layer-4 source port (uplink / client side).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Layer-4 destination port (downlink / server side).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Human-readable protocol name (e.g., "TCP", "UDP", "ICMP", "ICMPV6").</p></td></tr><tr><td><p><code>volume_uplink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Total payload volume transferred in the uplink (client → server) direction.</p></td></tr><tr><td><p><code>volume_downlink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Total payload volume transferred in the downlink (server → client) direction.</p></td></tr><tr><td><p><code>peak_volume_uplink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Peak uplink volume observed in a single reporting window.</p></td></tr><tr><td><p><code>peak_volume_downlink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Peak downlink volume observed in a single reporting window.</p></td></tr><tr><td><p><code>net_src_packets</code></p></td><td><p>uint64</p></td><td><p>packets</p></td><td><p>Total number of packets sent by the source (uplink).</p></td></tr><tr><td><p><code>net_dst_packets</code></p></td><td><p>uint64</p></td><td><p>packets</p></td><td><p>Total number of packets sent by the destination (downlink).</p></td></tr><tr><td><p><code>initial_direction</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Direction of the first packet in the flow: <code>"0"</code> = uplink, <code>"1"</code> = downlink.</p></td></tr></tbody></table>

### Direction Determination

Flow direction (uplink vs. downlink) is established using a priority-based approach:

1.  **Server Pool**: If a configured server pool contains one of the endpoints, direction is set accordingly.
2.  **TCP SYN Flag**: For TCP flows, the SYN initiator is classified as the client (uplink).
3.  **Port Heuristic**: The endpoint with the higher port number is assumed to be the client.
4.  **IP Comparison**: As a last resort, the lower IP address is assigned as the uplink side.

---

## **2\. TCP**

The TCP inspector creates a flow for each unique 5-tuple (src IP, dst IP, src port, dst port, protocol) and tracks the full lifecycle of the TCP connection through a state machine. It extracts detailed performance metrics for both client and server sides.

### 2.1 Connection Lifecycle KPIs

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>flow_state</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Current state of the TCP state machine (e.g., <code>"syn-sent"</code>, <code>"established"</code>, <code>"fin-wait"</code>, <code>"closed"</code>).</p></td></tr><tr><td><p><code>tcp_connection_id</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Unique hash identifier for this TCP connection (xxHash of the 5-tuple).</p></td></tr><tr><td><p><code>tcp_connection_requests</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of TCP connection initiation attempts (SYN packets sent).</p></td></tr><tr><td><p><code>tcp_connections_opened</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of successfully established connections (SYN-ACK handshake completed).</p></td></tr><tr><td><p><code>tcp_connections_failed</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of connection attempts that failed (e.g., RST received, timeout during handshake).</p></td></tr><tr><td><p><code>tcp_connections_active</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of connections currently in the established state (active data transfer).</p></td></tr><tr><td><p><code>tcp_connections_closed</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of connections that were gracefully closed (FIN handshake completed).</p></td></tr></tbody></table>

<br />

### **2.2 Timing KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>connection_time</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>TCP Connection Time</strong> — Time elapsed from the initial SYN to the completion of the three-way handshake (SYN → SYN-ACK → ACK). Measures how long it takes to establish the TCP connection.</p></td></tr><tr><td><p><code>tcp_time_to_first_byte</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Time to First Byte (TTFB)</strong> — Time from the completion of the TCP handshake to the first data packet received from the server. Indicates server processing responsiveness.</p></td></tr><tr><td><p><code>session_duration</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Session Duration</strong> — Total time from the first packet to the last packet in the TCP session. Reflects the overall lifetime of the connection.</p></td></tr></tbody></table>

<br />

### **2.3 Round-Trip Time & Jitter KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>tcp_rtt_client</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>Client RTT</strong> — Accumulated sum of round-trip time measurements from the client side. Computed by measuring the time between a data segment sent by the client and the corresponding ACK from the server.</p></td></tr><tr><td><p><code>tcp_rtt_client_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of client RTT samples collected. Mean RTT = <code>tcp_rtt_client / tcp_rtt_client_samples</code>.</p></td></tr><tr><td><p><code>tcp_rtt_server</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>Server RTT</strong> — Accumulated sum of round-trip time measurements from the server side. Measured from server data segments to their corresponding ACKs.</p></td></tr><tr><td><p><code>tcp_rtt_server_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of server RTT samples collected.</p></td></tr><tr><td><p><code>tcp_jitter_client</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>Client Jitter</strong> — Sum of absolute differences between consecutive RTT measurements on the client side. Measures RTT variability / network stability from the client's perspective.</p></td></tr><tr><td><p><code>tcp_jitter_client_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of client jitter samples. Mean jitter = <code>tcp_jitter_client / tcp_jitter_client_samples</code>.</p></td></tr><tr><td><p><code>tcp_jitter_server</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>Server Jitter</strong> — Sum of absolute RTT differences on the server side.</p></td></tr><tr><td><p><code>tcp_jitter_server_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of server jitter samples.</p></td></tr></tbody></table>

<br />

### **2.4 Data Transfer Time (DTT) KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>tcp_dtt_client</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>Client Data Transfer Time</strong> — Total time observed for data transfer operations initiated by the client. Captures the latency of client-side data delivery measured across groups of consecutive data packets.</p></td></tr><tr><td><p><code>tcp_dtt_client_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of client DTT samples.</p></td></tr><tr><td><p><code>tcp_dtt_server</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>Server Data Transfer Time</strong> — Total time observed for server-side data transfer operations. Captures server data delivery latency across groups of consecutive response packets.</p></td></tr><tr><td><p><code>tcp_dtt_server_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of server DTT samples.</p></td></tr></tbody></table>

<br />

### **2.5 Server Response Time (SRT)**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>tcp_srt_server</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>Server Response Time</strong> — Time between the last data packet from the client (request) and the first data packet from the server (response). Measures how quickly the server begins responding to client requests.</p></td></tr><tr><td><p><code>tcp_srt_server_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of SRT samples.</p></td></tr></tbody></table>

<br />

### **2.6 Retransmission KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>tcp_retransmissions_client</code></p></td><td><p>uint64</p></td><td><p>count (sum)</p></td><td><p><strong>Client Retransmissions</strong> — Number of retransmitted TCP segments detected on the client side. Detected by tracking sequence numbers: if a segment is sent with a sequence number lower than the next expected sequence, it is flagged as a retransmission.</p></td></tr><tr><td><p><code>tcp_retransmissions_client_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of reporting periods with client retransmission measurements.</p></td></tr><tr><td><p><code>tcp_retransmissions_server</code></p></td><td><p>uint64</p></td><td><p>count (sum)</p></td><td><p><strong>Server Retransmissions</strong> — Number of retransmitted segments on the server side.</p></td></tr><tr><td><p><code>tcp_retransmissions_server_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of reporting periods for server retransmissions.</p></td></tr><tr><td><p><code>tcp_retransmission_delay_client</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>Client Retransmission Delay</strong> — Accumulated delay caused by retransmissions on the client side. Measures the time between the original transmission and the retransmission of the same segment.</p></td></tr><tr><td><p><code>tcp_retransmission_delay_client_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of client retransmission delay samples.</p></td></tr><tr><td><p><code>tcp_retransmission_delay_server</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>Server Retransmission Delay</strong> — Accumulated retransmission delay on the server side.</p></td></tr><tr><td><p><code>tcp_retransmission_delay_server_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of server retransmission delay samples.</p></td></tr></tbody></table>

<br />

### **2.7 TCP Reset & Window KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>tcp_client_resets</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of TCP RST (reset) segments sent by the client. Indicates abnormal connection terminations or refused connections from the client side.</p></td></tr><tr><td><p><code>tcp_server_resets</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of TCP RST segments sent by the server.</p></td></tr><tr><td><p><code>tcp_window_size_client</code></p></td><td><p>uint64</p></td><td><p>bytes (sum)</p></td><td><p><strong>Client Window Size</strong> — Accumulated TCP receive window sizes advertised by the client. Used to detect window size trends and zero-window conditions.</p></td></tr><tr><td><p><code>tcp_window_size_client_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of client window size samples.</p></td></tr><tr><td><p><code>tcp_window_size_server</code></p></td><td><p>uint64</p></td><td><p>bytes (sum)</p></td><td><p><strong>Server Window Size</strong> — Accumulated receive window sizes advertised by the server.</p></td></tr><tr><td><p><code>tcp_window_size_server_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of server window size samples.</p></td></tr></tbody></table>

<br />

### **TCP Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>30 seconds</p></td><td><p>Time after last packet before a TCP flow is considered timed out.</p></td></tr><tr><td><p>Reporting Period</p></td><td><p>30 seconds</p></td><td><p>Interval at which live flow metrics are reported.</p></td></tr><tr><td><p>Reset Timeout</p></td><td><p>5 seconds</p></td><td><p>Shortened timeout applied when a TCP RST is detected.</p></td></tr></tbody></table>

---

## 3\. UDP

The UDP inspector creates flows based on the 5-tuple and tracks basic session metrics. Since UDP is connectionless, the metrics are simpler than TCP.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Source IP address (uplink side).</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Destination IP address (downlink side).</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Source port (uplink).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Destination port (downlink).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"UDP"</code>.</p></td></tr><tr><td><p><code>session_duration</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Duration of the UDP session, computed as the difference between the last and first packet timestamps. Used for throughput calculation: Throughput(UP) = volume_uplink / session_duration, Throughput(DOWN) = volume_downlink / session_duration.</p></td></tr><tr><td><p><code>flow_state</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Current state of the UDP flow: <code>"established"</code> (active) or <code>"finished"</code> (timed out or closed).</p></td></tr></tbody></table>

<br />

### **UDP Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>30 seconds</p></td><td><p>Time after last packet before a UDP flow is considered timed out.</p></td></tr><tr><td><p>Reporting Period</p></td><td><p>30 seconds</p></td><td><p>Interval for reporting live flow metrics.</p></td></tr></tbody></table>

---

## **4\. HTTP**

The HTTP inspector operates on top of TCP and parses HTTP request/response pairs using a state machine. It extracts metadata about web transactions.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>host</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>HTTP Host</strong> — Value of the HTTP <code>Host</code> header field. Non-ASCII characters are stripped. Identifies the web server or virtual host being accessed.</p></td></tr><tr><td><p><code>url</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Full URL</strong> — Constructed from the HTTP scheme, host, and URI path (e.g., <code>http://example.com/path/page</code>). Only reported if a URI is present. Non-ASCII characters are stripped.</p></td></tr><tr><td><p><code>http_status_code</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>HTTP Status Code</strong> — The response status code and reason phrase (e.g., <code>"200 OK"</code>, <code>"404 Not Found"</code>, <code>"503 Service Unavailable"</code>). Enables monitoring of error rates and server health.</p></td></tr></tbody></table>

<br />

### **HTTP Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>30 seconds</p></td><td><p>Inactivity timeout for HTTP flows.</p></td></tr><tr><td><p>HTTP Ports</p></td><td><p>80</p></td><td><p>Configurable list of TCP ports to inspect for HTTP traffic.</p></td></tr><tr><td><p>Web Requests Logging</p></td><td><p>Disabled</p></td><td><p>Optional logging of full web requests to an output directory.</p></td></tr></tbody></table>

---

## **5\. TLS / HTTPS**

The TLS inspector analyzes the TLS/SSL handshake to extract encryption metadata. It inspects up to the first 4 packets of a connection to parse the ClientHello and ServerHello messages.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>tls_version</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Negotiated TLS Version</strong> — The effective TLS/SSL version negotiated between client and server. Determined as the minimum of the maximum version supported by each side. Possible values: <code>"ssl-2.0"</code>, <code>"ssl-3.0"</code>, <code>"tls-1.0"</code>, <code>"tls-1.1"</code>, <code>"tls-1.2"</code>, <code>"tls-1.3"</code>. For TLS 1.3 detection, the <code>supported_versions</code> extension (type 43) in the ClientHello/ServerHello is inspected.</p></td></tr><tr><td><p><code>tls_server_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>TLS Server Name Indication (SNI)</strong> — The hostname requested by the client in the TLS ClientHello SNI extension (extension type 0). Allows identification of which HTTPS site is being accessed even though the traffic is encrypted. Non-ASCII characters are stripped.</p></td></tr><tr><td><p><code>host</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Same as <code>tls_server_name</code>. Reported under the generic <code>host</code> field for uniformity with HTTP flows.</p></td></tr></tbody></table>

<br />

### **TLS Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>TLS Port</p></td><td><p>443</p></td><td><p>TCP port monitored for TLS traffic.</p></td></tr><tr><td><p>Flow Timeout</p></td><td><p>5 seconds</p></td><td><p>TLS flow timeout (shorter since only the handshake is analyzed).</p></td></tr></tbody></table>

---

## **6\. DNS**

The DNS inspector performs deep packet inspection of DNS queries and responses, tracking resolution performance, flag states, and error conditions. It matches DNS queries with responses using the DNS transaction ID.

<br />

### **6.1 Query & Response Counters**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>dns_query_count</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total number of DNS question packets observed in this flow.</p></td></tr><tr><td><p><code>dns_response_count</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total number of DNS answer/response packets observed.</p></td></tr><tr><td><p><code>dns_rcode_ok_count</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of successful DNS responses (RCODE = 0, No Error). A high ratio of <code>rcode_ok_count / response_count</code> indicates healthy DNS resolution.</p></td></tr></tbody></table>

<br />

### **6.2 Performance KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>app_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>DNS RTT</strong> — Accumulated round-trip time of DNS resolutions. Computed as the time difference between a DNS question and its matching answer (matched by DNS transaction ID).</p></td></tr><tr><td><p><code>app_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of RTT measurements. Mean DNS RTT = <code>app_rtt / app_rtt_samples</code>.</p></td></tr><tr><td><p><code>app_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>DNS Jitter</strong> — Sum of absolute differences between consecutive DNS RTT measurements. Indicates variability in DNS resolution time.</p></td></tr><tr><td><p><code>app_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of jitter samples.</p></td></tr><tr><td><p><code>app_packet_loss</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>DNS Packet Loss</strong> — Number of DNS queries that did not receive a matching response (for finished flows), plus responses received without a matching query. Indicates DNS message loss or timeout.</p></td></tr></tbody></table>

<br />

### **6.3 Error KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>app_packet_err_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of malformed DNS packets detected in the uplink (query) direction.</p></td></tr><tr><td><p><code>app_packet_err_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of malformed DNS packets detected in the downlink (response) direction.</p></td></tr></tbody></table>

<br />

### **6.4 DNS Flags**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>dns_flag_response</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p><code>1</code> if the last DNS packet was a response, <code>0</code> if it was a query.</p></td></tr><tr><td><p><code>dns_flag_opcode</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p><code>1</code> if the DNS OPCODE is non-zero (non-standard query, e.g., inverse query or status request).</p></td></tr><tr><td><p><code>dns_flag_truncated</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>DNS TC (Truncation) flag. <code>1</code> if the response was truncated because it exceeded the maximum UDP message size.</p></td></tr><tr><td><p><code>dns_flag_authoritative</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>DNS AA (Authoritative Answer) flag. <code>1</code> if the responding server is authoritative for the queried domain.</p></td></tr><tr><td><p><code>dns_flag_recursion_desired</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>DNS RD (Recursion Desired) flag. <code>1</code> if the client requested recursive resolution.</p></td></tr><tr><td><p><code>dns_flag_recursion_available</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>DNS RA (Recursion Available) flag. <code>1</code> if the server supports recursive queries.</p></td></tr><tr><td><p><code>dns_flag_z</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>DNS Z (Reserved) flag. Should be zero in compliant implementations.</p></td></tr><tr><td><p><code>dns_flag_ad</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>DNS AD (Authenticated Data) flag. <code>1</code> if the response data has been verified by DNSSEC.</p></td></tr><tr><td><p><code>dns_flag_cd</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>DNS CD (Checking Disabled) flag. <code>1</code> if DNSSEC validation was disabled for this query.</p></td></tr><tr><td><p><code>dns_flag_reply_code</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>String representation of the DNS RCODE (e.g., <code>"No Error"</code>, <code>"NXDomain"</code>, <code>"ServFail"</code>, <code>"Refused"</code>).</p></td></tr></tbody></table>

<br />

### **6.5 Query & Answer Details**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>dns_query_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Domain name(s) in the DNS query. Multiple names are pipe-separated (e.g., `"example.com</p></td></tr><tr><td><p><code>dns_query_type</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>DNS query type(s) (e.g., <code>"A"</code>, <code>"AAAA"</code>, <code>"MX"</code>, <code>"CNAME"</code>, <code>"SRV"</code>, <code>"PTR"</code>, <code>"TXT"</code>). Multiple types are pipe-separated.</p></td></tr><tr><td><p><code>dns_query_class</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>DNS query class (typically <code>"IN"</code> for Internet). Multiple classes are pipe-separated.</p></td></tr><tr><td><p><code>dns_answer_address</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>IP address(es) returned in the DNS answer section. Multiple addresses are pipe-separated.</p></td></tr></tbody></table>

<br />

### **6.6 Application Identification**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Application name. Set to <code>"DNS"</code> for DNS flows. Additionally, DNS hostnames are matched against configurable regex signature rules (customer-specific and common) to classify applications via their DNS lookups. Matched entries are cached and associated with resolved IP addresses for subsequent flow classification.</p></td></tr></tbody></table>

<br />

### **DNS Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>DNS Port</p></td><td><p>53</p></td><td><p>UDP port monitored for DNS traffic.</p></td></tr><tr><td><p>Customer Regex Config</p></td><td><p>—</p></td><td><p>Path to customer-specific DNS hostname regex signature rules.</p></td></tr><tr><td><p>Common Regex Config</p></td><td><p>—</p></td><td><p>Path to common DNS hostname regex signature rules.</p></td></tr></tbody></table>

---

## **7\. SIP (VoIP Signaling)**

The SIP inspector provides comprehensive VoIP signaling analysis. It tracks the full lifecycle of SIP dialogs and produces KPIs aligned with telecom industry standards (ASR, NER, NEC). Each SIP flow is identified by a unique UUID and supports multi-dialog Call-ID tracking.

<br />

### **7.1 Call Attempt & Completion KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_call_attempts</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Call Attempts</strong> — Total number of call initiation attempts (INVITE messages sent), regardless of whether they succeed.</p></td></tr><tr><td><p><code>sip_answered_calls</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Answered Calls</strong> — Number of calls answered by the called party (INVITE followed by 200 OK). Used in NER (Network Effectiveness Ratio) and ASR (Answer-Seizure Ratio) calculations.</p></td></tr><tr><td><p><code>sip_successfully_ended_calls</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Successfully Ended Calls</strong> — Calls that completed the full lifecycle: INVITE → 200 OK → BYE. Indicates clean call completion without abnormal termination.</p></td></tr><tr><td><p><code>sip_dropped_call</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Dropped Calls</strong> — Calls where INVITE succeeded (200 OK received) but no BYE was observed, indicating an abnormal/premature termination.</p></td></tr><tr><td><p><code>sip_user_busy</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>User Busy</strong> — Calls rejected with SIP 486 (Busy Here). Used in NEC (Network Effectiveness Classification) and NER calculations.</p></td></tr><tr><td><p><code>sip_no_answer</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>No Answer</strong> — Calls that were cancelled or timed out without being answered. Used in NEC and NER calculations.</p></td></tr><tr><td><p><code>sip_terminal_reject</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Terminal Reject</strong> — Calls rejected with SIP 480 (Temporarily Unavailable). Used in NEC and NER calculations.</p></td></tr></tbody></table>

<br />

### **7.2 Call Duration KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_call_duration</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Call Duration</strong> — Length of the voice call from INVITE to BYE. Used for calculating Average Call Duration (ACD).</p></td></tr><tr><td><p><code>sip_short_duration_call</code></p></td><td><p>bool</p></td><td><p>flag</p></td><td><p><strong>Short Duration Call</strong> — Flag indicating the call duration was below a configurable threshold. Short calls may indicate network quality issues or robocall patterns.</p></td></tr><tr><td><p><code>sip_setup_duration</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Call Setup Duration</strong> — Time from the first accepted INVITE to the receipt of 200 OK (call answer). Reflects call setup latency / Post-Dial Delay (PDD).</p></td></tr></tbody></table>

<br />

### **7.3 INVITE Response KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_invite_any</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total INVITE requests sent (any).</p></td></tr><tr><td><p><code>sip_invite_200</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs answered with 200 OK (successful call setup).</p></td></tr><tr><td><p><code>sip_invite_3xx</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs receiving 3XX redirect responses.</p></td></tr><tr><td><p><code>sip_invite_480</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs receiving 480 (Temporarily Unavailable).</p></td></tr><tr><td><p><code>sip_invite_486</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs receiving 486 (Busy Here).</p></td></tr><tr><td><p><code>sip_invite_600</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs receiving 600 (Busy Everywhere).</p></td></tr><tr><td><p><code>sip_invite_603</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs receiving 603 (Decline).</p></td></tr><tr><td><p><code>sip_re_invite_attempts</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Re-INVITE Attempts</strong> — Number of INVITE packets sent after the first successful call setup (Re-INVITE). Used for mid-call changes such as codec renegotiation or call transfer.</p></td></tr></tbody></table>

<br />

### **7.4 REGISTER KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_register_any</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total REGISTER requests with any status response (excluding 401/402/407 auth challenges).</p></td></tr><tr><td><p><code>sip_register_ira</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Initial Registration Attempts</strong> — REGISTER requests followed by 4XX/5XX/6XX failure responses (excluding authentication challenges 401/402/407). Indicates registration failures.</p></td></tr><tr><td><p><code>sip_re_register_attempts_failed</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Failed Re-Registration Attempts</strong> — Subsequent REGISTER requests that failed after the initial registration.</p></td></tr><tr><td><p><code>sip_re_register_time</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Re-Registration Time</strong> — Time taken for re-registration procedures.</p></td></tr></tbody></table>

<br />

### **7.5 Other SIP Method KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_update_any</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total UPDATE requests sent. UPDATE modifies session parameters.</p></td></tr><tr><td><p><code>sip_update_200</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>UPDATE requests answered with 200 OK.</p></td></tr><tr><td><p><code>sip_subscribe_attempts</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total SUBSCRIBE requests (event notifications).</p></td></tr><tr><td><p><code>sip_notify_attempts</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total NOTIFY requests (event notification delivery).</p></td></tr></tbody></table>

<br />

### **7.6 SIP Event Timestamps**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_invite_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the INVITE request.</p></td></tr><tr><td><p><code>sip_trying_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the 100 Trying response.</p></td></tr><tr><td><p><code>sip_ringing_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the 180 Ringing response.</p></td></tr><tr><td><p><code>sip_invite_ok_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the INVITE 200 OK response (call answered).</p></td></tr><tr><td><p><code>sip_invite_failure_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the INVITE failure response (4XX–6XX, excluding 407 auth).</p></td></tr><tr><td><p><code>sip_bye_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the BYE request (call teardown initiation).</p></td></tr><tr><td><p><code>sip_bye_ok_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the BYE 200 OK response.</p></td></tr><tr><td><p><code>sip_cancel_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the CANCEL request.</p></td></tr><tr><td><p><code>sip_cancel_ok_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Timestamp of the CANCEL 200 OK response.</p></td></tr></tbody></table>

<br />

### **7.7 SIP Header Fields & Error KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_from</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>SIP <code>From</code> header field identifying the caller. Parsed once per dialog.</p></td></tr><tr><td><p><code>sip_to</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>SIP <code>To</code> header field identifying the called party.</p></td></tr><tr><td><p><code>sip_user_agent_client</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>User-Agent header from the UAC (client). Identifies the SIP client software (e.g., phone model, softphone application).</p></td></tr><tr><td><p><code>sip_user_agent_server</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>User-Agent header from the UAS (server). Identifies the SIP server or PBX software.</p></td></tr><tr><td><p><code>sip_failure_response_code</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>First failure response code received (4XX–6XX, excluding 407 auth). Saved once per dialog.</p></td></tr><tr><td><p><code>sip_reason</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>SIP <code>Reason</code> header (RFC 3326) providing machine-readable cause for call termination. May be empty.</p></td></tr><tr><td><p><code>sip_temporary_error_count</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of temporary error responses received during an INVITE transaction.</p></td></tr><tr><td><p><code>sip_call_state</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Final call state. Reported once per call: <code>"COMPLETED"</code>, <code>"BUSY"</code>, <code>"CANCELLED"</code>, <code>"NOT_AVAILABLE"</code>, <code>"TIMEDOUT"</code>.</p></td></tr></tbody></table>

<br />

### **7.8 SIP Packet Counters**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_packet_count_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total SIP packets in the uplink direction.</p></td></tr><tr><td><p><code>sip_packet_count_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total SIP packets in the downlink direction.</p></td></tr><tr><td><p><code>sip_packet_count_segmented_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Segmented (incomplete/split) SIP packets in uplink. Indicates SIP messages spanning multiple TCP segments.</p></td></tr><tr><td><p><code>sip_packet_count_segmented_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Segmented SIP packets in downlink.</p></td></tr><tr><td><p><code>sip_packet_count_error_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Malformed / empty / corrupt SIP packets in uplink.</p></td></tr><tr><td><p><code>sip_packet_count_error_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Malformed SIP packets in downlink.</p></td></tr><tr><td><p><code>sip_packet_count_retrans_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Retransmitted SIP packets in uplink. SIP retransmission is detected at the application layer.</p></td></tr><tr><td><p><code>sip_packet_count_retrans_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Retransmitted SIP packets in downlink.</p></td></tr><tr><td><p><code>sip_packet_count_compound_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Compound SIP packets (multiple SIP messages in a single packet) in uplink.</p></td></tr><tr><td><p><code>sip_packet_count_compound_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Compound SIP packets in downlink.</p></td></tr></tbody></table>

<br />

### **7.9 VoIP Call Sequence Diagram**

The SIP inspector also generates a VoIP Call Sequence Diagram as a CSV-formatted XDR file for visual call flow analysis:

<table><tbody><tr><th><p>CSV Field</p></th><th><p>Description</p></th></tr><tr><td><p><code>timestamp</code></p></td><td><p>Packet timestamp</p></td></tr><tr><td><p><code>sip_call_id</code></p></td><td><p>SIP Call-ID header</p></td></tr><tr><td><p><code>ip_src</code> / <code>ip_dst</code></p></td><td><p>Source and destination IP addresses</p></td></tr><tr><td><p><code>srcport</code> / <code>dstport</code></p></td><td><p>Source and destination ports</p></td></tr><tr><td><p><code>proto</code></p></td><td><p>Transport protocol (TCP/UDP)</p></td></tr><tr><td><p><code>phone_from</code> / <code>phone_to</code></p></td><td><p>Phone numbers extracted from SIP From/To headers</p></td></tr><tr><td><p><code>sip_from</code> / <code>sip_to</code></p></td><td><p>Full SIP From/To fields</p></td></tr><tr><td><p><code>msg</code></p></td><td><p>SIP message (request method name or response status code)</p></td></tr><tr><td><p><code>comment</code></p></td><td><p>Sequence diagram annotation</p></td></tr><tr><td><p><code>raw_sip_line</code></p></td><td><p>First line of the raw SIP message</p></td></tr></tbody></table>

<br />

### **SIP Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>SIP Port</p></td><td><p>5060</p></td><td><p>Port monitored for SIP traffic (TCP and UDP).</p></td></tr><tr><td><p>Flow Timeout</p></td><td><p>5 seconds</p></td><td><p>Inactivity timeout for SIP flows. Configurable via XML.</p></td></tr></tbody></table>

---

## **8\. RTP / RTCP (VoIP Media)**

The RTP inspector provides the most comprehensive set of KPIs in the system, measuring real-time media quality for VoIP calls. All metrics are reported per-direction (uplink/downlink) to allow independent assessment of each audio stream. The inspector is tightly integrated with the SIP inspector via shared data structures for call correlation.

<br />

### **8.1 Identification & Codec KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Application label: <code>"RTP"</code> for RTP streams, <code>"RTCP"</code> for RTCP-only flows.</p></td></tr><tr><td><p><code>voip_uuid</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>UUID linking this RTP stream to its parent SIP flow.</p></td></tr><tr><td><p><code>sip_call_id</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>SIP Call-ID of the associated VoIP call.</p></td></tr><tr><td><p><code>rtp_ssrc_up</code></p></td><td><p>string</p></td><td><p>hex</p></td><td><p><strong>SSRC (Synchronization Source)</strong> — Uplink stream SSRC identifier in hexadecimal. Uniquely identifies the RTP stream within the session.</p></td></tr><tr><td><p><code>rtp_ssrc_down</code></p></td><td><p>string</p></td><td><p>hex</p></td><td><p>Downlink SSRC identifier.</p></td></tr><tr><td><p><code>rtp_encoding_name_up</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Codec Name</strong> — Audio codec used in the uplink direction (e.g., <code>"PCMU"</code>, <code>"PCMA"</code>, <code>"G729"</code>, <code>"OPUS"</code>, <code>"AMR"</code>). For dynamic payload types, reported as <code>"RTP-Type-XX"</code> where XX is the payload type number.</p></td></tr><tr><td><p><code>rtp_encoding_name_down</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Audio codec used in the downlink direction.</p></td></tr><tr><td><p><code>rtp_payload_type_up</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>RTP payload type number for the uplink (0–127). Static types (0–95) have fixed codec mappings; dynamic types (96–127) are resolved via SDP negotiation.</p></td></tr><tr><td><p><code>rtp_payload_type_down</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>RTP payload type number for the downlink.</p></td></tr><tr><td><p><code>rtp_sample_rate_up</code></p></td><td><p>int</p></td><td><p>Hz</p></td><td><p>Audio sample rate for the uplink codec (e.g., 8000, 16000, 48000 Hz).</p></td></tr><tr><td><p><code>rtp_sample_rate_down</code></p></td><td><p>int</p></td><td><p>Hz</p></td><td><p>Audio sample rate for the downlink.</p></td></tr><tr><td><p><code>rtp_channels_up</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>Number of audio channels in uplink (1 = mono, 2 = stereo).</p></td></tr><tr><td><p><code>rtp_channels_down</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>Number of audio channels in downlink.</p></td></tr></tbody></table>

<br />

### **8.2 Packet Count KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_packet_count_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total RTP packets received in the uplink direction.</p></td></tr><tr><td><p><code>rtp_packet_count_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total RTP packets in the downlink direction.</p></td></tr><tr><td><p><code>rtp_rtcp_packet_count_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total RTCP packets in the uplink direction.</p></td></tr><tr><td><p><code>rtp_rtcp_packet_count_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total RTCP packets in the downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_lost_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Lost Packets</strong> — RTP packets lost in the uplink, detected by gaps in the RTP sequence number. Uses the RFC 3550 algorithm with wrap-around handling.</p></td></tr><tr><td><p><code>rtp_packet_count_lost_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Lost packets in the downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_dup_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Duplicate Packets</strong> — RTP packets with a sequence number already seen (duplicates).</p></td></tr><tr><td><p><code>rtp_packet_count_dup_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Duplicate packets in the downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_ooo_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Out-of-Order Packets</strong> — RTP packets arriving out of sequence order in the uplink.</p></td></tr><tr><td><p><code>rtp_packet_count_ooo_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Out-of-order packets in the downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_error_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Invalid RTP Packets</strong> — Packets that failed RTP validation in the uplink.</p></td></tr><tr><td><p><code>rtp_packet_count_error_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Invalid RTP packets in the downlink.</p></td></tr><tr><td><p><code>rtcp_packet_count_error_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Invalid RTCP packets in the uplink.</p></td></tr><tr><td><p><code>rtcp_packet_count_error_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Invalid RTCP packets in the downlink.</p></td></tr></tbody></table>

<br />

### **8.3 Payload-Specific Counters**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_packet_count_codec_change_real_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Real Codec Changes</strong> — Number of times the audio codec changed during the stream (excluding Comfort Noise and DTMF). Indicates mid-call codec renegotiation.</p></td></tr><tr><td><p><code>rtp_packet_count_codec_change_real_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Real codec changes in the downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_codec_change_any_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Any Codec Changes</strong> — All payload type changes including transitions to/from Comfort Noise and DTMF.</p></td></tr><tr><td><p><code>rtp_packet_count_codec_change_any_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Any codec changes in the downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_marker_bit_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Marker Bit Packets</strong> — Packets with the RTP marker bit set, typically indicating the start of a talkspurt after silence.</p></td></tr><tr><td><p><code>rtp_packet_count_marker_bit_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Marker bit packets in the downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_cn_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Comfort Noise Packets</strong> — RTP packets carrying Comfort Noise (CN) payload, generated during silence periods in voice calls.</p></td></tr><tr><td><p><code>rtp_packet_count_cn_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Comfort Noise packets in the downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_dtmf_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>DTMF Packets</strong> — RTP packets carrying DTMF telephone events (RFC 4733).</p></td></tr><tr><td><p><code>rtp_packet_count_dtmf_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>DTMF packets in the downlink.</p></td></tr></tbody></table>

<br />

### **8.4 Jitter KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_jitter_interarrival_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Interarrival Jitter</strong> — RFC 3550 Jitter computed as the statistical variance of RTP packet inter-arrival times in the uplink. Formula: `J(i) = J(i-1) + (</p></td></tr><tr><td><p><code>rtp_jitter_interarrival_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Interarrival jitter in the downlink.</p></td></tr><tr><td><p><code>rtp_jitter_mean_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Mean Jitter</strong> — Average of all jitter measurements across the stream in the uplink.</p></td></tr><tr><td><p><code>rtp_jitter_mean_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Mean jitter in the downlink.</p></td></tr><tr><td><p><code>rtp_jitter_max_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Maximum Jitter</strong> — Highest jitter value observed in the uplink stream. Indicates worst-case timing variation.</p></td></tr><tr><td><p><code>rtp_jitter_max_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Maximum jitter in the downlink.</p></td></tr></tbody></table>

<br />

### **8.5 Delta (Packet Arrival Interval) KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_delta_mean_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Mean Delta</strong> — Average time between consecutive RTP packet arrivals in the uplink. Nominal value depends on codec (e.g., 20 ms for G.711). Deviations indicate network delays or buffering.</p></td></tr><tr><td><p><code>rtp_delta_mean_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Mean delta in the downlink.</p></td></tr><tr><td><p><code>rtp_delta_max_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Maximum Delta</strong> — Largest inter-packet arrival gap in the uplink. Indicates the worst burst of delay or packet gap.</p></td></tr><tr><td><p><code>rtp_delta_max_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Maximum delta in the downlink.</p></td></tr></tbody></table>

<br />

### **8.6 Skew (Timestamp Drift) KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_skew_mean_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Mean Skew</strong> — Average drift between RTP timestamps and actual packet arrival times in the uplink. Positive skew means packets arrive faster than expected; negative means slower. Measured in units of the codec sample rate.</p></td></tr><tr><td><p><code>rtp_skew_mean_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Mean skew in the downlink.</p></td></tr><tr><td><p><code>rtp_skew_max_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Maximum Skew</strong> — Peak timestamp drift observed in the uplink.</p></td></tr><tr><td><p><code>rtp_skew_max_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Maximum skew in the downlink.</p></td></tr></tbody></table>

<br />

### **8.7 Bandwidth KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_bandwidth_mean_up</code></p></td><td><p>double</p></td><td><p>kbps</p></td><td><p><strong>Mean Bandwidth</strong> — Average RTP stream bandwidth in the uplink, computed over a 1-second sliding window of payload bytes.</p></td></tr><tr><td><p><code>rtp_bandwidth_mean_down</code></p></td><td><p>double</p></td><td><p>kbps</p></td><td><p>Mean bandwidth in the downlink.</p></td></tr><tr><td><p><code>rtp_bandwidth_max_up</code></p></td><td><p>double</p></td><td><p>kbps</p></td><td><p><strong>Maximum Bandwidth</strong> — Peak 1-second bandwidth observed in the uplink.</p></td></tr><tr><td><p><code>rtp_bandwidth_max_down</code></p></td><td><p>double</p></td><td><p>kbps</p></td><td><p>Maximum bandwidth in the downlink.</p></td></tr><tr><td><p><code>rtp_total_volume_up</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p><strong>Total Volume</strong> — Cumulative RTP payload bytes in the uplink.</p></td></tr><tr><td><p><code>rtp_total_volume_down</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Total payload bytes in the downlink.</p></td></tr></tbody></table>

<br />

### **8.8 Quality (MOS / R-Factor) KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_mos_up</code></p></td><td><p>double</p></td><td><p>score</p></td><td><p><strong>Mean Opinion Score (MOS)</strong> — Estimated voice quality score for the uplink (1.0–5.0 scale). Computed from RTCP Receiver Report statistics using the E-model algorithm. Only reported if ≥ 1.0. Higher values indicate better quality: 4.0+ = Toll quality, 3.5+ = Acceptable.</p></td></tr><tr><td><p><code>rtp_mos_down</code></p></td><td><p>double</p></td><td><p>score</p></td><td><p>MOS for the downlink stream.</p></td></tr><tr><td><p><code>rtp_r_factor_up</code></p></td><td><p>double</p></td><td><p>—</p></td><td><p><strong>R-Factor</strong> — ITU-T G.107 E-model R-factor for the uplink (0–100 scale). Combines effects of codec, delay, loss, and jitter into a single quality metric. R &gt; 80 = High quality, R &gt; 70 = Medium, R &gt; 60 = Low, R &lt; 50 = Poor.</p></td></tr><tr><td><p><code>rtp_r_factor_down</code></p></td><td><p>double</p></td><td><p>—</p></td><td><p>R-Factor for the downlink.</p></td></tr><tr><td><p><code>rtp_rtt_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Round-Trip Time</strong> — RTT between endpoints as measured from RTCP Sender/Receiver Reports (SR/RR). Only reported if &gt; 0.</p></td></tr><tr><td><p><code>rtp_rtt_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>RTT in the downlink.</p></td></tr><tr><td><p><code>rtp_transit_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Transit Time</strong> — One-way transit delay estimated as RTT/2.</p></td></tr><tr><td><p><code>rtp_transit_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Transit time in the downlink.</p></td></tr></tbody></table>

<br />

### **8.9 Clock & Frequency Drift KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_clock_drift_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Clock Drift</strong> — Accumulated clock drift between the sender's RTP clock and the receiver's wall clock in the uplink. Computed via linear regression of arrival times vs. RTP timestamps. Formula: <code>drift = 1000 duration (clock_ratio - 1.0)</code>.</p></td></tr><tr><td><p><code>rtp_clock_drift_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Clock drift in the downlink.</p></td></tr><tr><td><p><code>rtp_freq_drift_hz_up</code></p></td><td><p>double</p></td><td><p>Hz</p></td><td><p><strong>Frequency Drift</strong> — Drift expressed in Hz relative to the nominal sample rate. Formula: <code>clock_ratio * sample_rate</code>.</p></td></tr><tr><td><p><code>rtp_freq_drift_hz_down</code></p></td><td><p>double</p></td><td><p>Hz</p></td><td><p>Frequency drift in the downlink.</p></td></tr><tr><td><p><code>rtp_freq_drift_percentage_up</code></p></td><td><p>double</p></td><td><p>%</p></td><td><p><strong>Frequency Drift Percentage</strong> — Drift as a percentage of the nominal sample rate. Formula: <code>100 * (clock_ratio - 1.0)</code>.</p></td></tr><tr><td><p><code>rtp_freq_drift_percentage_down</code></p></td><td><p>double</p></td><td><p>%</p></td><td><p>Frequency drift percentage in the downlink.</p></td></tr></tbody></table>

<br />

### **8.10 Sequence Number & Duration KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_seq_first_up</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>First RTP sequence number seen in the uplink stream.</p></td></tr><tr><td><p><code>rtp_seq_first_down</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>First sequence number in the downlink.</p></td></tr><tr><td><p><code>rtp_seq_last_up</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Last RTP sequence number seen in the uplink.</p></td></tr><tr><td><p><code>rtp_seq_last_down</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Last sequence number in the downlink.</p></td></tr><tr><td><p><code>rtp_seq_err_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Sequence Errors</strong> — Total sequence anomalies (lost + duplicate + out-of-order) in the uplink.</p></td></tr><tr><td><p><code>rtp_seq_err_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Sequence errors in the downlink.</p></td></tr><tr><td><p><code>rtp_ts_first_up</code></p></td><td><p>uint32</p></td><td><p>RTP ts</p></td><td><p>First RTP timestamp value in the uplink.</p></td></tr><tr><td><p><code>rtp_ts_first_down</code></p></td><td><p>uint32</p></td><td><p>RTP ts</p></td><td><p>First RTP timestamp in the downlink.</p></td></tr><tr><td><p><code>rtp_ts_last_up</code></p></td><td><p>uint32</p></td><td><p>RTP ts</p></td><td><p>Last RTP timestamp in the uplink.</p></td></tr><tr><td><p><code>rtp_ts_last_down</code></p></td><td><p>uint32</p></td><td><p>RTP ts</p></td><td><p>Last RTP timestamp in the downlink.</p></td></tr><tr><td><p><code>rtp_duration_up</code></p></td><td><p>double</p></td><td><p>seconds</p></td><td><p><strong>Stream Duration</strong> — Duration of the uplink RTP stream.</p></td></tr><tr><td><p><code>rtp_duration_down</code></p></td><td><p>double</p></td><td><p>seconds</p></td><td><p>Duration of the downlink stream.</p></td></tr></tbody></table>

<br />

### **8.11 DTMF (Telephone Event) KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_dtmf_tones_up</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>DTMF Tone Sequence</strong> — String of DTMF events detected in the uplink (e.g., <code>"1234567890*#ABCD"</code>). Each character represents a detected DTMF digit.</p></td></tr><tr><td><p><code>rtp_dtmf_tones_down</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>DTMF tones in the downlink.</p></td></tr><tr><td><p><code>rtp_dtmf_tones_volume_min_up</code></p></td><td><p>int</p></td><td><p>dBm</p></td><td><p><strong>Minimum DTMF Volume</strong> — Lowest volume level of DTMF events in the uplink (higher numerical values indicate lower volume).</p></td></tr><tr><td><p><code>rtp_dtmf_tones_volume_min_down</code></p></td><td><p>int</p></td><td><p>dBm</p></td><td><p>Minimum DTMF volume in the downlink.</p></td></tr><tr><td><p><code>rtp_dtmf_tones_volume_max_up</code></p></td><td><p>int</p></td><td><p>dBm</p></td><td><p><strong>Maximum DTMF Volume</strong> — Highest volume level of DTMF events in the uplink.</p></td></tr><tr><td><p><code>rtp_dtmf_tones_volume_max_down</code></p></td><td><p>int</p></td><td><p>dBm</p></td><td><p>Maximum DTMF volume in the downlink.</p></td></tr></tbody></table>

<br />

### **RTP Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>5 seconds</p></td><td><p>Inactivity timeout for RTP streams.</p></td></tr><tr><td><p>Ports</p></td><td><p>Dynamic</p></td><td><p>RTP ports are not statically configured; they are discovered through SDP negotiation in SIP signaling.</p></td></tr></tbody></table>

---

## **9\. ICMP**

The ICMP inspector tracks Echo Request/Reply (ping) flows and computes round-trip performance metrics based on matching request-response pairs.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Source IP (echo requester).</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Destination IP (echo responder).</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>ICMP Identifier field (used as a pseudo-port for flow identification).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Same ICMP Identifier field.</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"ICMP"</code>.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"ICMP"</code>.</p></td></tr><tr><td><p><code>icmp_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>ICMP RTT</strong> — Sum of round-trip times measured by matching ICMP Echo Requests (type 8) with Echo Replies (type 0).</p></td></tr><tr><td><p><code>icmp_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of RTT samples.</p></td></tr><tr><td><p><code>app_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p>Same as <code>icmp_rtt</code>, reported under the generic application RTT field.</p></td></tr><tr><td><p><code>app_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Same as <code>icmp_rtt_samples</code>.</p></td></tr><tr><td><p><code>icmp_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>ICMP Jitter</strong> — Sum of absolute differences between consecutive RTT measurements.</p></td></tr><tr><td><p><code>icmp_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of jitter samples.</p></td></tr><tr><td><p><code>app_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p>Same as <code>icmp_jitter</code>, generic application jitter field.</p></td></tr><tr><td><p><code>app_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Same as <code>icmp_jitter_samples</code>.</p></td></tr><tr><td><p><code>icmp_min_rtt</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Minimum RTT</strong> — Lowest round-trip time observed in the flow.</p></td></tr><tr><td><p><code>icmp_max_rtt</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Maximum RTT</strong> — Highest round-trip time observed.</p></td></tr><tr><td><p><code>icmp_packet_loss</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>ICMP Packet Loss</strong> — Number of unmatched Echo Requests (no corresponding Reply received).</p></td></tr><tr><td><p><code>app_packet_loss</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Same as <code>icmp_packet_loss</code>, generic field.</p></td></tr></tbody></table>

<br />

### **ICMP Direction Logic**

-   ICMP type 8 (Echo Request) → classified as **uplink**
-   All other ICMP types → classified as **downlink**

<br />

### **ICMP Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>15 seconds</p></td><td><p>Inactivity timeout for ICMP flows.</p></td></tr><tr><td><p>Reporting Period</p></td><td><p>30 seconds</p></td><td><p>Reporting interval.</p></td></tr></tbody></table>

---

## **10\. ICMPv6**

The ICMPv6 inspector mirrors ICMP functionality for IPv6 networks, tracking Echo Request/Reply pairs and computing performance metrics for IPv6 ping operations.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Source IPv6 address (echo requester).</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Destination IPv6 address (echo responder).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"ICMPV6"</code>.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"ICMPV6"</code>.</p></td></tr><tr><td><p><code>icmp_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>ICMPv6 RTT</strong> — Sum of round-trip times from Echo Request (type 128) to Echo Reply (type 129).</p></td></tr><tr><td><p><code>icmp_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of RTT samples.</p></td></tr><tr><td><p><code>app_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p>Generic RTT field.</p></td></tr><tr><td><p><code>app_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>RTT sample count.</p></td></tr><tr><td><p><code>icmp_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>ICMPv6 Jitter</strong> — Sum of absolute RTT differences.</p></td></tr><tr><td><p><code>icmp_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Jitter sample count.</p></td></tr><tr><td><p><code>app_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p>Generic jitter field.</p></td></tr><tr><td><p><code>app_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Jitter sample count.</p></td></tr><tr><td><p><code>icmp_min_rtt</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Minimum RTT observed.</p></td></tr><tr><td><p><code>icmp_max_rtt</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Maximum RTT observed.</p></td></tr><tr><td><p><code>icmp_packet_loss</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Unmatched Echo Requests (packet loss).</p></td></tr><tr><td><p><code>app_packet_loss</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Generic packet loss field.</p></td></tr></tbody></table>

<br />

### **ICMPv6 Direction Logic**

-   ICMPv6 type 128 (Echo Request) → classified as **uplink**
-   All other types → classified as **downlink**

<br />

### **ICMPv6 Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>15 seconds</p></td><td><p>Inactivity timeout.</p></td></tr><tr><td><p>Reporting Period</p></td><td><p>30 seconds</p></td><td><p>Reporting interval.</p></td></tr></tbody></table>

---

## **11\. DHCP**

The DHCP inspector tracks DHCP transactions by matching packets using the transaction ID (XID). It monitors DHCP handshake performance and detects packet errors.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Client IP address (uplink).</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Server IP address (downlink).</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Client port (typically 68).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Server port (typically 67).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"DHCP"</code>.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"DHCP"</code>.</p></td></tr><tr><td><p><code>app_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>DHCP RTT</strong> — Round-trip time of DHCP transactions (e.g., DISCOVER → OFFER, REQUEST → ACK). Matched using the DHCP transaction ID (XID).</p></td></tr><tr><td><p><code>app_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of RTT samples.</p></td></tr><tr><td><p><code>app_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (sum)</p></td><td><p><strong>DHCP Jitter</strong> — Variability between consecutive DHCP transaction RTTs.</p></td></tr><tr><td><p><code>app_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of jitter samples.</p></td></tr><tr><td><p><code>app_packet_loss</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>DHCP Packet Loss</strong> — Unmatched DHCP requests (no corresponding server response).</p></td></tr><tr><td><p><code>app_packet_err_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Malformed DHCP packets in the uplink direction.</p></td></tr><tr><td><p><code>app_packet_err_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Malformed DHCP packets in the downlink direction.</p></td></tr></tbody></table>

<br />

### **DHCP Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>5 seconds</p></td><td><p>Inactivity timeout for DHCP flows.</p></td></tr><tr><td><p>Reporting Period</p></td><td><p>30 seconds</p></td><td><p>Reporting interval.</p></td></tr><tr><td><p>Min Packet Size</p></td><td><p>240 bytes</p></td><td><p>Minimum accepted DHCP packet length.</p></td></tr></tbody></table>

---

## **12\. DHCPv6**

The DHCPv6 inspector handles DHCP for IPv6 networks, tracking transactions by the 24-bit transaction ID field. It validates DHCPv6 message types (1–13 per RFC 8415) and ports (546 client, 547 server).

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Client IPv6 address.</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Server IPv6 address.</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Client port (546).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Server port (547).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"DHCP"</code>.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"DHCP"</code>.</p></td></tr><tr><td><p><code>app_packet_err_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Invalid DHCPv6 packets in the uplink (wrong message type, invalid length, etc.).</p></td></tr><tr><td><p><code>app_packet_err_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Invalid DHCPv6 packets in the downlink.</p></td></tr></tbody></table>

<br />

### **DHCPv6 Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>5 seconds</p></td><td><p>Inactivity timeout.</p></td></tr><tr><td><p>Min Packet Size</p></td><td><p>4 bytes</p></td><td><p>Minimum packet size (message type + transaction ID).</p></td></tr></tbody></table>

---

## **13\. TWAMP**

The TWAMP (Two-Way Active Measurement Protocol, RFC 5357) inspector supports both the control protocol (TCP port 862) and test protocol (dynamic UDP ports). It measures one-way delay and jitter between TWAMP sender and reflector endpoints.

<br />

### **13.1 TWAMP Control Protocol States**

The inspector implements the full TWAMP control state machine:

<table><tbody><tr><th><p>State</p></th><th><p>Description</p></th></tr><tr><td><p><code>GREETING</code></p></td><td><p>Server sends 64-byte greeting message.</p></td></tr><tr><td><p><code>SETUP_RESPONSE</code></p></td><td><p>Client responds with setup parameters.</p></td></tr><tr><td><p><code>SERVER_START</code></p></td><td><p>Server confirms session start.</p></td></tr><tr><td><p><code>REQUEST_SESSION</code></p></td><td><p>Client requests a test session (sender/receiver ports extracted).</p></td></tr><tr><td><p><code>ACCEPT_SESSION</code></p></td><td><p>Server accepts (receiver port confirmed).</p></td></tr><tr><td><p><code>START_SESSIONS</code></p></td><td><p>Client starts test sessions.</p></td></tr><tr><td><p><code>START_SESSIONS_ACK</code></p></td><td><p>Server acknowledges test start.</p></td></tr><tr><td><p><code>STOP_SESSIONS</code></p></td><td><p>Client stops test sessions.</p></td></tr></tbody></table>

<br />

### **13.2 TWAMP Test KPIs**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>twamp_sender_packet_number</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of test packets sent by the TWAMP sender. Reset after each report.</p></td></tr><tr><td><p><code>twamp_receiver_packet_number</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of test packets received by the TWAMP reflector. Reset after each report.</p></td></tr><tr><td><p><code>twamp_delay</code></p></td><td><p>int64</p></td><td><p>ns (sum)</p></td><td><p><strong>One-Way Delay</strong> — Accumulated one-way delay measurements. Computed from TWAMP timestamps: <code>delay = receiver_t2 - sender_t2 - (receiver_t1 - receiver_t0)</code>. Matched by sequence numbers.</p></td></tr><tr><td><p><code>twamp_delay_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of delay measurements. Mean delay = <code>twamp_delay / twamp_delay_samples</code>.</p></td></tr><tr><td><p><code>jitter</code></p></td><td><p>int64</p></td><td><p>ns (sum)</p></td><td><p><strong>TWAMP Jitter</strong> — Sum of absolute differences between consecutive delay measurements. Formula: `</p></td></tr><tr><td><p><code>jitter_samples</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Number of jitter measurements.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Always <code>"twamp-test"</code>.</p></td></tr></tbody></table>

<br />

### **TWAMP Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Control Port</p></td><td><p>862</p></td><td><p>TCP port for TWAMP control protocol.</p></td></tr><tr><td><p>Flow Timeout</p></td><td><p>5 seconds</p></td><td><p>Inactivity timeout.</p></td></tr></tbody></table>

---

## **14\. FTP**

The FTP inspector identifies FTP control and data connections and tracks passive/active mode data channel establishment. It classifies FTP flows and parses control messages to dynamically discover FTP data connections.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>FTP application signature. Always <code>"ftp"</code> regardless of whether it is a control or data connection.</p></td></tr></tbody></table>

<br />

### **FTP Detection Logic**

<table><tbody><tr><th><p>Port</p></th><th><p>Type</p></th><th><p>Description</p></th></tr><tr><td><p>21</p></td><td><p>Control</p></td><td><p>FTP control channel (commands and responses).</p></td></tr><tr><td><p>20</p></td><td><p>Data</p></td><td><p>FTP data channel (file transfers).</p></td></tr><tr><td><p>Dynamic</p></td><td><p>Data (passive)</p></td><td><p>Discovered via parsing <code>PASV</code> (227) responses on the control channel.</p></td></tr><tr><td><p>Dynamic</p></td><td><p>Data (active)</p></td><td><p>Discovered via parsing <code>PORT</code> commands on the control channel.</p></td></tr></tbody></table>

<br />

### **FTP Control Message Parsing**

The inspector parses FTP control messages including:

-   **PORT command**: Extracts client IP and port for active mode data connections (format: `PORT h1,h2,h3,h4,p1,p2`).
-   **227 (Passive Mode)**: Extracts server IP and port for passive mode data connections.
-   **226 (Transfer Complete)**: Detects successful file transfer completion.
-   **426 (Transfer Aborted)**: Detects aborted transfers.

---

## **15\. GRE**

The GRE (Generic Routing Encapsulation) inspector decapsulates GRE tunnels, allowing the analysis of inner (encapsulated) traffic. The inspector extracts the GRE header fields and chains to the appropriate inner protocol inspector.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>gre_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>GRE Protocol Type</strong> — The EtherType of the encapsulated protocol (e.g., <code>0x0800</code> for IPv4, <code>0x86DD</code> for IPv6).</p></td></tr></tbody></table>

<br />

### **GRE Header Fields Parsed**

<table><tbody><tr><th><p>Field</p></th><th><p>Size</p></th><th><p>Description</p></th></tr><tr><td><p>Flags &amp; Version</p></td><td><p>2 bytes</p></td><td><p>GRE flags including checksum-present (bit 15) and key-present (bit 13).</p></td></tr><tr><td><p>Protocol Type</p></td><td><p>2 bytes</p></td><td><p>EtherType of the inner protocol.</p></td></tr><tr><td><p>Checksum</p></td><td><p>2 bytes</p></td><td><p>Optional; present if checksum flag is set.</p></td></tr><tr><td><p>Reserved</p></td><td><p>2 bytes</p></td><td><p>Optional; present with checksum.</p></td></tr><tr><td><p>Key</p></td><td><p>4 bytes</p></td><td><p>Optional tunnel key; present if key flag is set.</p></td></tr></tbody></table>

After decapsulation, the inner packet is handed to the appropriate IP inspector for full protocol analysis, so all inner-protocol KPIs (TCP, UDP, etc.) are reported as nested metrics of the GRE flow.

---

## **16\. Application Layer (DPI)**

The Application Layer inspector uses Deep Packet Inspection (DPI) to classify traffic by application. It combines multiple identification techniques: payload signature matching, DNS-based classification, and DPDK-based 5-tuple classification.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Application Name</strong> — Identified application name from the DPI engine or DNS-based classification (e.g., <code>"youtube"</code>, <code>"facebook"</code>, <code>"netflix"</code>). Defaults to <code>"generic-app"</code> if unidentified.</p></td></tr><tr><td><p><code>app_code</code></p></td><td><p>uint32</p></td><td><p>—</p></td><td><p><strong>Application Code</strong> — Numeric application identifier combining a group code (11 bits, up to 2048 groups) and application code (21 bits, up to ~2M apps). Encoded as `(group_code &lt;&lt; 21)</p></td></tr><tr><td><p><code>dpi_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>DPI engine classification name.</p></td></tr><tr><td><p><code>policy_id</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Network policy ID associated with the flow (from DPDK classifier).</p></td></tr><tr><td><p><code>policy_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Human-readable policy name.</p></td></tr><tr><td><p><code>first_pph</code></p></td><td><p>uint64</p></td><td><p>—</p></td><td><p><strong>First Packet Payload Hash</strong> — 64-bit hash of the first data packet payload. Used for traffic fingerprinting and signature matching.</p></td></tr><tr><td><p><code>packet_ports</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Packet Ports</strong> — Semicolon-separated list of port names observed in the flow.</p></td></tr><tr><td><p><code>volume_uplink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Application payload volume in the uplink direction.</p></td></tr><tr><td><p><code>volume_downlink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Application payload volume in the downlink direction.</p></td></tr><tr><td><p><code>net_src_packets</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Uplink packet count at the application layer.</p></td></tr><tr><td><p><code>net_dst_packets</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Downlink packet count.</p></td></tr></tbody></table>

<br />

### **DPI Classification Process**

1.  **Payload Inspection** (first 8 packets): DPI signatures are applied against the packet payload until an application is identified or 8 packets have been inspected.
2.  **DNS Pre-Classification**: Hostnames from DNS responses are matched against configurable regex signature rules. IPs resolved from matching hostnames are cached, and subsequent flows to those IPs inherit the application classification.
3.  **DPDK 5-Tuple Classification**: Hardware-accelerated ACL rules classify flows by 5-tuple for policy enforcement.

<br />

### **Application DPI Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>30 seconds</p></td><td><p>Application flow inactivity timeout.</p></td></tr><tr><td><p>Reporting Period</p></td><td><p>30 seconds</p></td><td><p>Reporting interval.</p></td></tr><tr><td><p>Signature Reload</p></td><td><p>60 seconds</p></td><td><p>Interval to check for updated DPI signature files.</p></td></tr><tr><td><p>Max Scan Length</p></td><td><p>2000 bytes</p></td><td><p>Maximum payload bytes scanned per packet for regex signatures.</p></td></tr></tbody></table>

---

## **17\. Other L4 Protocols**

The "Other L4" inspector handles IP protocols that are not TCP, UDP, ICMP, ICMPv6, or GRE. It provides basic flow tracking and identification using a protocol lookup table.

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Source IP address.</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Destination IP address.</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Source port (set to 0 for non-port protocols).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Destination port (set to 0).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Protocol name from lookup table (e.g., <code>"SCTP"</code>, <code>"OSPF"</code>, <code>"PIM"</code>, <code>"OTHER"</code>).</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Uppercase protocol name.</p></td></tr></tbody></table>

<br />

### **Other L4 Configuration**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>30 seconds</p></td><td><p>Inactivity timeout.</p></td></tr><tr><td><p>Reporting Period</p></td><td><p>30 seconds</p></td><td><p>Reporting interval.</p></td></tr></tbody></table>

---

## **Appendix: Inspector Chain Architecture**

The system processes packets through a chain of protocol inspectors, where each inspector handles one protocol layer and delegates to the next:

```
Ethernet Inspector
  ├── VLAN Inspector (802.1Q / MPLS)
  │     └── IP Inspector
  ├── IP Inspector (IPv4)
  │     ├── IPv6 Inspector (tunneled)
  │     ├── TCP Inspector
  │     │     ├── HTTP Inspector
  │     │     ├── TLS Inspector
  │     │     ├── SIP Inspector
  │     │     ├── FTP Inspector
  │     │     └── TWAMP Inspector (control)
  │     ├── UDP Inspector
  │     │     ├── DNS Inspector
  │     │     ├── SIP Inspector
  │     │     ├── RTP Inspector
  │     │     ├── DHCP Inspector
  │     │     ├── DHCPv6 Inspector
  │     │     └── TWAMP Inspector (test)
  │     ├── ICMP Inspector
  │     ├── GRE Inspector → (re-enters IP Inspector)
  │     ├── IP Inspector (IP-in-IP)
  │     └── Other L4 Inspector
  └── IPv6 Inspector
        ├── TCP Inspector → (same sub-tree as above)
        ├── UDP Inspector → (same sub-tree as above)
        ├── ICMPv6 Inspector
        └── Other L4 Inspector
```

The **Application (DPI) Inspector** operates as a separate overlay layer, receiving flows from TCP and UDP inspectors and performing deep packet inspection for application identification.

Each flow is uniquely identified by a hash of its 5-tuple (source IP, destination IP, source port, destination port, protocol) and VLAN ID, computed using the xxHash algorithm. Flow state is maintained across packets and reported at configurable intervals or upon flow termination.