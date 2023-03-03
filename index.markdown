---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: Not Your Average App

---

# Mobile Browsers

Mobile browsers occupy a unique space in the mobile ecosystem.
They enable users to browse the Internet and are responsible for various functions in this process.
More specifically, due to this special position, browsers enjoy access to various _Personally Identifiable Information (PII)._
More specifically they can access the following:

* User browsing data
  * Browsing history
  * Login information

* Mobile-specific Data
  * GPS
  * Camera
  * Microphone
  * Non-Resettable identifiers (IMEI, MAC ID, etc.)
  * Resettable identifiers (Ad ID)


With this access to such sensitive user data, browsers get to **harm** users or **protect** them.

---

# Harms To Users

The harms we look for in this project are described below.


**Unnecessary Data Sharing:**
Browsers may share the aforementioned data (IMEI, AdID, Android ID, etc.) with first parties (browser developers) or third parties (data brokers, advertisers, analytics companies).
Such sharing could be for various purposes many of which would harm user privacy.

**Website Manipulation:**
Browsers could modify the content they show users in such a way that they harm user perception of this content.
This is harmful to users.

**Insufficient Connection Security:**
Browsers that fail to implement basic connection security (specifically HTTPS) would expose users to risks on the internet, specifically MITM attacks.

# Protections For Users

The protections we look for are described below.

**Blocking Tracking Domains:**
Browsers could protect user privacy by blocking domains that track users as they browse the Internet.

**Limiting Access to WebAPIs:**
WebAPIs allow websites to access a number of user data (including mic, camera, etc.); thus sufficiently protecting these with permission controls is crucial to protecting users on the Internet.

**Upgrading Connection Security:**
Browsers can protect users by upgrading web communications to HTTPS whenever supported by servers in order to protect users.

---

# Testing Framework

We first collect 424 *Android* browsers from a number of sources:
* Google Play Store
* 360
* Anzhi
* Appchina
* Tencent

![Testing Framework](/assets/framework.png)

We install browsers on a physical Android device and instrument them to visit multiple websites while collecting all traffic with [mitmproxy](https://mitmproxy.org/) allowing us to answer if browsers **harm** or **protect** users.

---

# Results

### Browsing History Collection

* ~3% (13 of 424) of browsers send browsing history to endpoints on the Internet along with one or more identifiers
* ~9% (37 of 424) share browsing history with endpoints where purpose cannot be ascertained (based on publicly available information)
* ~14% (60 of 424) share browsing history related to known browsing features (sitecheck, suggestions, search, etc.)

Popular browsers that collect history include Opera, Yandex Browser, and UC Browser.

### Observed PII Exposure

* 2% Google Play and 6% Chinese Browsers collect non-resettable identifiers, which is extremely harmful to user privacy.
* 32% browsers collect at least one identifier, resettable and/or non-resettable.


### Improper TLS Implementation

Improper TLS implementations expose users of browsers to arbitrary *machine in the middle(mitm)* attacks, which is highly dangerous.

10% browsers are vulnerable to such attacks.

Further details and results can be found in the [paper](https://petsymposium.org/popets/2023/popets-2023-0003.pdf).

---

# Press

Links available soon.

---

## [PETS 2023 Paper](https://petsymposium.org/popets/2023/popets-2023-0003.pdf)

Not Your Average App: A Large-scale Privacy Analysis of Android Browsers *PETS 2023*,
*Amogh Pradeep (Northeastern University), Álvaro Feal (IMDEA Networks / Universidad Carlos III de Madrid), Julien Gamba (IMDEA Networks / Universidad Carlos III de Madrid), Ashwin Rao (University of Helsinki), Martina Lindorfer (TU Wien), Narseo Vallina-Rodriguez (IMDEA Networks / ICSI / AppCensus Inc.), and David Choffnes (Northeastern University)*

---

This work was supported by the National Science Foundation (Grants: SaTC-1618955 and ProperData SaTC-1955227).
