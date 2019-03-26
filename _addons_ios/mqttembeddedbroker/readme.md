---
id: mqttembeddedbroker
label: MQTT Broker Moquette
title: MQTT Broker Moquette - System Integrations
type: io
description: "MQTT is a machine-to-machine (M2M)/'Internet of Things' connectivity protocol. It was designed as an extremely lightweight publish/subscribe messaging transport."
since: 2x
install: manual
---

<!-- Attention authors: Do not edit directly. Please add your changes to the appropriate source repository -->

{% include base.html %}

# MQTT Broker Moquette

    MQTT is a machine-to-machine (M2M)/"Internet of Things" connectivity protocol. It was designed as an extremely lightweight publish/subscribe messaging transport.

To allow MQTT capable devices to communicate with each other you need a software called MQTT Broker.

You can either install one of the many MQTT Broker offerings or use this pre-configured Broker called [Moquette](https://github.com/andsel/moquette).

Check your Inbox after installation.

## Service Configuration

All parameters are optional and can be set by file or the REST interface (user-interfaces).

* __port__: The port, the embedded broker should run on. Defaults to not set, which means the typical ports 1883 and 8883 (SSL) are used.
* __username__: The user name that clients need to provide to connect to this broker.
* __password__: The password that clients need to provide to connect to this broker.
* __secure__: If set, hosts a secure SSL connection on port 8883 or otherwise a non secure connection on port 1883 (if not overwritten by the port parameter).
* __persistence_file__: An optional persistence file. Retained messages are stored in this file. Can be empty to not store anything. The default is "userdata/mqttembedded.bin". If it starts with "/" on Linux/MacOS or with a drive letter and colon (eg "c:/") it will be treated as an absolute path. Be careful to select a path that you have write access to.

## TLS connections

The keystore that is included to allow to start a TLS encrypted connection is generated by:

```keytool -genkey -v -keystore serverkeystore.keystore -alias main -keyalg RSA -keysize 2048 -validity 100000 -deststoretype pkcs12
```

The keystore is embedded into the bundle and cannot be replaced. This may change in the future as soon as openHAB
gained a way to configure SSL truststores framework wide.

## Plans for the future

The moquette MQTT broker supports ACL (access control lists), so allows to restrict read/write access per user or
client id. That need to be exposed as configuration values at some point.

Multiple users are supported by the broker software. openHAB does not yet have a user management though.