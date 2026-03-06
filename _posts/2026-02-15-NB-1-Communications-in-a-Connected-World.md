---
layout: post
title: NB 1 Communications in a Connected World
date: 2026-02-15
description: overview of network communication concepts, including network types, data transmission, and the fundamentals of bandwidth and throughput.
tags: networks review
# categories: sample-posts
categories: networks
featured: false
toc:
  beginning: true
---

* Topics
  - Network Types
  - Data Transmission
  - Bandwidth and Throughput

---

##### <mark style="background-color: #87CEEB;">A. Network Types </mark>

* Everything is Online
  - Devices today are expected to always be connected to the global internet.
  - The internet is used to interact and communicate with others.
  - The internet is not a physical place but a **collection of connections**.
  - It is a platform to **find and share information**.

* Who owns the Internet?
  - No single entity owns the internet.
  - It is a **worldwide collection of interconnected networks**.
  - Networks cooperate to exchange information using **common standards (protocols)**.
  - Connections use:
    - Telephone wires
    - Fiber-optic cables
    - Wireless transmissions
    - Satellite links
  - All online resources exist somewhere within the global internet.
  - These destinations connect to **local networks** that send and receive data.

1. <u>Mobile Devices</u>
  * The internet connects devices used daily, such as:
  - Mobile phones
  - Smartwatches
  - Smart glasses
  - Other smart home devices

1. <u>Connected Home Devices</u>
  * Many home devices can connect to the internet for **remote monitoring**, including:
  - Security systems
  - Appliances
  - Smart TVs
  - Gaming consoles

1. <u>Other Connected Devices</u>
  * Devices outside the home also connect to networks, including:
  * Examples
    - Smart cars
    - RFID tags
    - Sensors and actuators
    - Medical devices
  * Sensors and Actuators
    - **Sensors** detect environmental conditions:
      - Temperature
      - Humidity
      - Pressure
      - Soil moisture
    - **Actuators** perform actions based on sensor data:
      - Example: triggering irrigation when soil is dry

1. <u>Local Networks</u>
  - Networks come in many sizes.
  - They can range from **two computers** to **hundreds of thousands of devices**.

  * Small Office/Home Office (SOHO) Networks
    - Used in small offices or homes.
    - Allow sharing of resources such as:
      - Printers
      - Documents
      - Pictures
      - Music
    - Networks provide faster and cheaper communication than traditional methods.
    - Enable rapid communication such as:
      - Email
      - Instant messaging
    - Provide centralized access to information stored on servers.

  * Small Home Networks
    - Connect a few devices together such as:
      - Computers
      - Printers
      - Internet connection
  
  * Small Office and Home Office Networks (SOHO)
    - Allow home or remote office computers to connect to a **corporate network**.
    - Enable access to **centralized shared resources**.
  
  * Medium to Large Networks
    - Used by organizations such as:
      - Corporations
      - Schools
    - May connect **hundreds or thousands of hosts across multiple locations**.
  
  * Worldwide Networks
    - The **internet** itself.
    - A **network of networks** connecting millions of computers worldwide.

---

##### <mark style="background-color: #87CEEB;">B. Data Transmission</mark>

* What is Data?
  - Data is **raw information** that users send, share, or upload.

1. <u>Types of (Personal) Data</u>
* Volunteered Data
  - Data willingly shared by individuals.
* Inferred Data
  - Data generated from user activities.
  - Often collected without the user realizing.
  - Example: Credit card transactions showing preferences or locations.
* Observed Data
  - Data collected and stored automatically.
  - Example:
    - Location data from mobile applications.

2. <u>The Bit</u>
* Computers operate using **binary digits (bits)**:  
  - **0** or **1**
* A bit can represent:
  - Two voltage levels
  - On or off states
  - Input devices convert human actions into binary.
  - Output devices convert binary into human-readable information.

--- 

ASCII (American Standard Code for Information Interchange)
: A common binary encoding system.

Examples:
- A = `0100 0001`
- 9 = `0011 1001`
- (#) = `0010 0011`

- **8 bits = 1 byte**

---

##### <mark style="background-color: #87CEEB;"> C. Methods of Data Transmission</mark>

* After data becomes binary, it must be converted into **signals**.
* Transmission Media
  - Signals travel through different media such as:
    - Copper wires
    - Fiber-optic cables
    - Wireless electromagnetic waves
  - Signals may travel as:
    - Electrical pulses
    - Light pulses
    - Radio waves
* Signals may be converted multiple times before reaching the destination.

1. <u>Three Common Signal Transmission Methods</u>

  * Electrical Signals
    - Data transmitted as electrical pulses through copper wires.

  * Optical Signals
    - Electrical signals converted into **light pulses** using fiber-optic cables.

  * Wireless Signals
    - Data transmitted using:
      - Infrared
      - Microwave
      - Radio waves

  * Most homes and small businesses use:
    - Copper cables
    - Wi-Fi wireless connections

  * Large networks often use **fiber-optic cables** for longer distances.

---

##### <mark style="background-color: #87CEEB;"> D. Bandwidth and Throughput</mark>

* Different media support data transfer at different speeds.
* Two key measurements:
  - **Throughput**
  - **Bandwidth**

1. <u>Throughput</u>
  * Throughput measures the **actual amount of data successfully transferred over time**.
  * Throughput is usually **lower than bandwidth** because of factors such as:
    - Network traffic
    - Type of data transmitted
    - Network device delays

1. <u>Bandwidth</u>

  * Bandwidth refers to the **capacity of a network medium to carry data**

  * Digital Bandwidth 
    - Measures the amount of data that can travel between two points over time
    * Common Units: 
      - Kbps – thousands of bits per second
      - Mbps – millions of bits per second
      - Gbps – billions of bits per second
  
  * Factors Affecting Bandwidth
    - Physical properties of the medium
    - Current technology
    - Laws of physics
<br><br>

* Latency
  - Latency is the **time delay for data to travel from source to destination**.

* Network Limitation
  - In a network path:
    - Throughput cannot exceed the **slowest link** in the network.

---

##### <mark style="background-color: #87CEEB;"> E. Internet Speed Tests</mark>

* Tools used to measure network performance include:
  - Speedtest.net

* Measurements include:
  - **Download speed** – bits received per second
  - **Upload speed** – bits sent per second

* These tools measure performance across:
  - Local networks
  - Internet service providers
  - Internet connections

---

##### <mark style="background-color: #87CEEB;"> Summary </mark>

* <u>Network Types</u>
  - The internet is a **global network of interconnected networks**.
  - Networks exchange data using **standard protocols**.
  - Connections may use:
    - Wired cables
    - Fiber-optic cables
    - Wireless transmission
    - Satellite links
  - SOHO networks connect home or small office devices.
  - Large networks connect organizations across multiple locations.
<br><br>

* <u>Data Transmission</u>
  - Types of Personal Data
    - **Volunteered data** – intentionally shared
    - **Observed data** – collected by monitoring actions
    - **Inferred data** – derived from analyzing other data
<br><br>

* <u>Bit</u>
  - Smallest unit of data
  - Represented as **0 or 1**
<br><br>

* <u>Transmission Methods</u>
  - Electrical signals
  - Optical signals
  - Wireless signals
<br><br>

* <u>Bandwidth and Throughput</u>
  - Bandwidth
    - Maximum data capacity of a medium
    - Measured in:
      - Kbps
      - Mbps
      - Gbps

  - Throughput
    - Actual data transferred
    - Influenced by:
      - Network traffic
      - Latency
      - Network device delays
<br><br>

* <u>Latency</u>
  - Time delay for data to travel between two points.

---

##### <mark style="background-color: #87CEEB;"> Reflection </mark>
- The internet is a **massive network of networks** connected directly or indirectly.
- It can be visualized like a **spider’s web**, where many connections link the systems together.




