---
layout: post
title: "The Connectivity of Things"
categories: blog
excerpt: "Notes from IOTcon 2014"
tags: [iot, conferences]
author: hlgr360
share: true
---

Here are my notes from [IOTcon 2014](http://iotcon.de/2014/de) in Berlin. Feel free to ping me if anything catches your interest and you want to talk about it.

It was a more developer focussed conference than Thingscon with an heavy emphasize on Protocols and Frameworks (in particular Eclipse hosted ones). One interesting and very mature looking framework I did not know was [OpenHAB](http://www.openhab.org).

#### M2M, IoT and Device Mgmt - One Protocol to bind them all

* General
  * M2M: device to server
  * IoT: everything to the cloud
  * WoT
    * IP address for everything (Mesh Network - RPL RFC 6550)
    * REST for everything (Mashup applications)
* Application Protocols: MQTT, Coap, XMPP
  * MQTT
    * topics for data and actions
    * security: username/password, TLS over TCP (RFC5246)
    * Eclipse projects: Mosquitto, Moquette, Palo, Ponte, Kura
  * Coap
    * RFC7252
    * targets 1$ 8bit MPU
    * over UDP, maps transparently to HTTP
    * supports concept of observer (pubsub)
    * discoverability
      * Based on weblinking (RFC5988)
      * Extended core linking format (RFC6690)
    * decentralized
      * multicast, multiple registries
    * security
      * DTLS (TLS for Datagram) with focus on ECC
      * RFC6347
    * Eclipse projects: Californium
  * Embedded challenges
    * TLS/DTLS complexity and code size
    * Arduino Uno can run Coap/MQTT but not securely
    * IETF Dice group is working on TLS for embedded
      * Tiny DTLS (Sourceforge) MIT licensed
      * Eclipse Scandium as subproject of Californium
    * Security challenges
      * provisioning of device key from factory to server (million of devices with different keys)
      * bootstrapping of key material in the field
* Device Management
  * everything a gateway needs for operating a fleet of IoT devices
    * monitoring, configuring, securing, updating
    * interoperability will be key
  * protocols
    * TR-609
      * SOAP API (HTTPS + XML)
      * designed for home gateways and set top boxes
    * OMA-DM
      * designed for mobile phones but also M2M
      * target users are network operators
      * HTTP + XML, security is MD5 HMAC (because of HMAC no streaming possible)
    * Lightweight M2M (LWM2M)
      * OMA-DM for M2M
      * uses Coap
      * Different API endpoints for security, device, common, location, firmware, etc
        * object has numerical identifier
        * /[object]/[instance]/[resource]
          * 6/0/ (complete location)
          * 6/0/2 (only altitude of location)
        * secure bootstrapping and well-defined security life cycle
          * device is shipped with bootstrap server credentials
          * bootstrap server provisiones device keys
  * Eclipse project: Wakaama (client lib in C), Leshan (server lib in Java)
* Protocol convergence
  * securing and provisioning is hard problem
  * LWM2M + Coap
    * Gateway as aggregator and hiding Coap endpoints on devices
    * Coap creates REST endpoints on device for remote access

#### From washing machines to power plants:

* Network topologies
  * local (is it part of IoT?)
  * local + gateway (gateway is accessible form outside)
  * cloud (remote server - big (aggregated) data analysis becomes possible)
  * cloud + gateway (most common)
* Data is not like traffic
  * See RFC1149 and RFC2149 for avian communication protocol :)
  * New communication paradigm: publish/subscribe
* Device IoT Apps are hard
  * Application Protocol
    * HTTP (Websocket), Coap (Observer), MQTT (native)
  * Data Format
    * XML/EXI (tree), N3/RDF (graph), Json/MsgPack/Protobuf/Bysant/BSON (object)
  * Device identification and privacy
* Lego-based approach
  * Eclipse Ponte as HTTP (REST), MQTT, Coap bridge
  * https://github.com/mcollina/ascoltatori (pub/sub lib for node.js)
  * https://github.com/mcollina/mosca (mqtt broker for node.js)

#### Embeddable Sensor Networks (demo)

* components
  * XBEE2 (from Digi) as sensor nodes building mesh network
  * RPi as mesh coordinator and bridge to MQTT
  * Beaglebone Black as MQTT broker
  * Cubieboard 2 for data storage (incl. SATA2 interface for SDD, MongoDB for ARM)
  * RPi with 2.8'' LCD touch display as UI (using Java FX)
* Use of MQTT to decouple components

#### Securing the IoT (WSO2)

* What is different about IoT
  * Longevity of devices
  * Size of device
  * No UI, no user inputs
  * Data - often highly personal
* Challenges
  * security through obscurity
  * IETF code sizes for various crypto libs and lags
    * http://tools.ietf.org/html/draft-aks-crypto-sensors-02
  * http://www.slideshare.net/cpswan/security-protocols-in-constrained-environments
  * No encryption / security shield for Arduino
  * Key distribution
    * usually at manufacturing time
    * complex to update
  * Password suck for humans, they suck even more for devices
    * Tim Bray: OAuth2 token are like a hotel room key
    * https://www.tbray.org/ongoing/When/201x/2013/05/24/Access-Token-Hotel-Key
  * Federated Identity
    * meaningful consent mechanism
    * use Oauth token for use in API calls instead of password
    * bootstrapping through device mgmt
    * oauth plugin for Mosquitto MQTT broker
      * http://pzf.fremantle.org/2013/11/using-oauth-20-with-mqtt.html
      * https://groups.google.com/forum/#!msg/mqtt/Y1KnH3F8uuw/JC4a9sJi0icJ
    * put oauth token on device
    * scope to be limited to topics the device can publish to
    * support token refresh
* Checkout GSMA Mobile Connect (http://gsmamobileeconomy.com/gsmamc/)
  * mobile alternative to OpenID Connect ?
* WSO2 Reference Architecture for IoT
  * http://www.slideshare.net/wso2.org/io-t-referencearchitecturewebinar