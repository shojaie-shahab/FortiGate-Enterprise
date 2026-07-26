# FortiGate NSE4 Complete Documentation

یک مرجع جامع آموزشی برای یادگیری FortiGate و FortiOS بر اساس مفاهیم دوره NSE4.

این پروژه با هدف ایجاد یک Documentation فارسی و ساختاریافته طراحی شده است. هر مفهوم مهم در یک فایل Markdown مستقل توضیح داده می‌شود تا امکان مطالعه عمیق، توسعه محتوا، اضافه کردن دیاگرام، سناریوهای عملی و مثال‌های واقعی وجود داشته باشد.

ساختار این Repository بر اساس مفاهیم اصلی FortiGate طراحی شده است، نه صرفاً ترتیب سرفصل‌های آزمون. هدف اصلی، ایجاد یک مرجع آموزشی کامل برای یادگیری، پیاده‌سازی و عیب‌یابی FortiGate در محیط‌های واقعی شبکه است.

---

# Documentation Structure

## 01. Fortinet & FortiGate Fundamentals

**فایل:** `01-Fortinet-FortiGate-Fundamentals.md`

این فصل به معرفی Fortinet، معماری FortiGate، ساختار داخلی FortiOS و مفاهیم پایه‌ای مورد نیاز برای درک عملکرد Firewall می‌پردازد. در این بخش با اکوسیستم Fortinet، معماری پردازشی FortiGate، سخت‌افزار دستگاه‌ها و نحوه عملکرد سیستم‌عامل FortiOS آشنا خواهید شد.

**مباحث این فصل:**

- What is Fortinet
- Company Overview
- Product Portfolio
- Fortinet Ecosystem
- FortiGuard Services
- FortiCare Services
- Security Fabric Overview
- FortiGate Architecture
- Control Plane
- Data Plane
- Management Plane
- Packet Flow Architecture
- Kernel
- Proxy Mode
- Flow Mode
- FortiGate Hardware
- Desktop Models
- Rack Models
- Chassis Models
- NP ASIC
- CP ASIC
- SoC Processors
- Memory
- Storage
- Interfaces
- Console Port
- HA Ports
- FortiOS
- Configuration Database
- CLI Structure
- GUI Overview
- VDOM Architecture
- Boot Process
- Firmware Images
- Upgrade Path
- Backup & Restore

➡️ **مطالعه فصل:** [01-Fortinet-FortiGate-Fundamentals.md](01-Fortinet-FortiGate-Fundamentals.md)

---

## 02. Deployment & Initial Setup

**فایل:** `02-Deployment-Initial-Setup.md`

این فصل نحوه استقرار FortiGate در محیط‌های مختلف، انجام تنظیمات اولیه، پیکربندی Interfaceها و روش‌های دسترسی مدیریتی را بررسی می‌کند. هدف این بخش آماده‌سازی FortiGate برای استفاده در شبکه‌های واقعی است.

**مباحث این فصل:**

- Deployment Models
- Physical Appliance
- Virtual Machine
- Cloud Deployment
- Transparent Mode
- NAT Mode
- Initial Configuration
- Factory Default
- First Login
- Change Password
- Hostname
- Timezone
- DNS
- NTP
- FortiGuard Configuration
- Interface Configuration
- Physical Interface
- VLAN Interface
- Loopback Interface
- Tunnel Interface
- Aggregate Interface
- Redundant Interface
- Hardware Switch
- Software Switch
- Administrative Access
- HTTPS
- HTTP
- SSH
- Telnet
- PING
- SNMP
- Administrative Profiles
- Trusted Hosts

➡️ **مطالعه فصل:** [02-Deployment-Initial-Setup.md](02-Deployment-Initial-Setup.md)

---

## 03. Routing

**فایل:** `03-Routing.md`

این فصل مفاهیم مسیریابی در FortiGate را از مبانی اولیه تا Routing پیشرفته بررسی می‌کند. در این بخش نحوه تصمیم‌گیری FortiOS برای انتخاب مسیر، مدیریت Routeها و استفاده از پروتکل‌های مسیریابی بررسی خواهد شد.

**مباحث این فصل:**

- Routing Fundamentals
- Routing Table
- Route Lookup
- Administrative Distance
- Priority
- ECMP
- Static Routing
- Default Route
- Blackhole Route
- Floating Static Route
- Recursive Route
- Dynamic Routing
- OSPF
- BGP
- RIP
- Policy Routing
- Policy Route
- Use Cases
- Route Decision Order

➡️ **مطالعه فصل:** [03-Routing.md](03-Routing.md)

---

## 04. Firewall

**فایل:** `04-Firewall.md`

این فصل مهم‌ترین بخش عملکرد FortiGate یعنی پردازش Firewall Traffic را پوشش می‌دهد. در این بخش نحوه عبور Packetها، ایجاد Session، انتخاب Policy، اعمال Security Profileها و مدیریت Objectهای شبکه بررسی می‌شود.

**مباحث این فصل:**

- Packet Flow
- Session Creation
- Route Lookup
- Policy Lookup
- NAT Processing
- Security Profile Inspection
- Session Close
- Firewall Policy
- Source
- Destination
- Service
- Schedule
- Action
- Logging
- NAT
- Security Profiles
- Policy Order
- Implicit Deny
- Zones
- Address Objects
- Address
- Address Group
- FQDN
- Geography
- Dynamic Address
- Service Objects
- Service
- Service Group
- Internet Service Database (ISDB)

➡️ **مطالعه فصل:** [04-Firewall.md](04-Firewall.md)

---

## 05. NAT

**فایل:** `05-NAT.md`

این فصل به بررسی کامل مکانیزم NAT در FortiGate اختصاص دارد. در این بخش نحوه تغییر آدرس‌ها، انتشار سرویس‌های داخلی، Port Forwarding و سناریوهای مختلف NAT بررسی می‌شود.

**مباحث این فصل:**

- NAT Concepts
- Source NAT
- Destination NAT
- Virtual IP (VIP)
- Port Forwarding
- Central NAT
- Hairpin NAT

➡️ **مطالعه فصل:** [05-NAT.md](05-NAT.md)

---
## 06. Authentication

**فایل:** `06-Authentication.md`

این فصل به بررسی روش‌های مختلف احراز هویت کاربران در FortiGate و نحوه اتصال آن به سرویس‌های هویتی سازمانی می‌پردازد. در این بخش با روش‌های Local Authentication، اتصال به سرویس‌های خارجی مانند LDAP و RADIUS، استفاده از Certificate و پیاده‌سازی احراز هویت چندمرحله‌ای آشنا خواهید شد.

**مباحث این فصل:**

- Local Users
- User Groups
- LDAP
- RADIUS
- TACACS+
- PKI Authentication
- Certificate Authentication
- Multi-Factor Authentication
- FSSO

➡️ **مطالعه فصل:** [06-Authentication.md](06-Authentication.md)

---

## 07. VPN

**فایل:** `07-VPN.md`

این فصل به بررسی کامل قابلیت‌های VPN در FortiGate اختصاص دارد. در این بخش معماری VPN، فرآیند ایجاد تونل‌های امن، روش‌های رمزنگاری، احراز هویت و سناریوهای مختلف اتصال کاربران و سایت‌ها بررسی می‌شود.

**مباحث این فصل:**

- IPsec VPN
- VPN Concepts
- IKE
- Phase 1
- Phase 2
- Encryption Algorithms
- DH Groups
- PFS
- DPD
- Route-based VPN
- Policy-based VPN
- Dial-up VPN
- SSL VPN
- SSL VPN Overview
- Tunnel Mode
- Web Mode
- Portal
- Authentication
- Split Tunnel
- Full Tunnel
- Bookmarks

➡️ **مطالعه فصل:** [07-VPN.md](07-VPN.md)

---

## 08. SD-WAN

**فایل:** `08-SD-WAN.md`

این فصل معماری SD-WAN در FortiGate و نحوه مدیریت هوشمند چندین لینک WAN را بررسی می‌کند. در این بخش با انتخاب مسیر بر اساس کیفیت لینک، بررسی سلامت ارتباطات، Failover و Load Balancing آشنا خواهید شد.

**مباحث این فصل:**

- SD-WAN Architecture
- Members
- Zones
- SLA
- Performance SLA
- Health Check
- SD-WAN Rules
- Link Cost
- Failover
- Load Balancing
- Implicit Rule

➡️ **مطالعه فصل:** [08-SD-WAN.md](08-SD-WAN.md)

---

## 09. Security Profiles

**فایل:** `09-Security-Profiles.md`

این فصل به معرفی موتورهای امنیتی FortiGate می‌پردازد. در این بخش نحوه عملکرد قابلیت‌هایی مانند Antivirus، IPS، Web Filtering، Application Control و SSL Inspection بررسی می‌شود که نقش اصلی را در محافظت از شبکه در برابر تهدیدات ایفا می‌کنند.

**مباحث این فصل:**

- Antivirus
- Scan Mode
- Archive Scan
- Outbreak Prevention
- IPS
- Signature
- Sensors
- Protocol Decoders
- Rate Based Signatures
- Web Filter
- Category Filter
- URL Filter
- Static URL
- FortiGuard Categories
- DNS Filter
- Application Control
- SSL Inspection
- Certificate Inspection
- Deep Inspection
- Email Filter
- File Filter
- DLP
- ICAP

➡️ **مطالعه فصل:** [09-Security-Profiles.md](09-Security-Profiles.md)

---

## 10. High Availability

**فایل:** `10-High-Availability.md`

این فصل به بررسی معماری High Availability در FortiGate اختصاص دارد. در این بخش نحوه ایجاد کلاسترهای FortiGate، هماهنگی بین اعضا، همگام‌سازی اطلاعات، فرآیند Failover و جلوگیری از اختلال سرویس‌ها بررسی می‌شود.

**مباحث این فصل:**

- HA Overview
- Active Passive
- Active Active
- FGCP
- Heartbeat
- Session Pickup
- Override
- HA Priority
- Failover Process
- Split Brain
- Reserved Management Interface

➡️ **مطالعه فصل:** [10-High-Availability.md](10-High-Availability.md)

---
## 06. Authentication

**فایل:** `06-Authentication.md`

این فصل به بررسی روش‌های مختلف احراز هویت کاربران در FortiGate و نحوه اتصال آن به سرویس‌های هویتی سازمانی می‌پردازد. در این بخش با روش‌های Local Authentication، اتصال به سرویس‌های خارجی مانند LDAP و RADIUS، استفاده از Certificate و پیاده‌سازی احراز هویت چندمرحله‌ای آشنا خواهید شد.

**مباحث این فصل:**

- Local Users
- User Groups
- LDAP
- RADIUS
- TACACS+
- PKI Authentication
- Certificate Authentication
- Multi-Factor Authentication
- FSSO

➡️ **مطالعه فصل:** [06-Authentication.md](06-Authentication.md)

---

## 07. VPN

**فایل:** `07-VPN.md`

این فصل به بررسی کامل قابلیت‌های VPN در FortiGate اختصاص دارد. در این بخش معماری VPN، فرآیند ایجاد تونل‌های امن، روش‌های رمزنگاری، احراز هویت و سناریوهای مختلف اتصال کاربران و سایت‌ها بررسی می‌شود.

**مباحث این فصل:**

- IPsec VPN
- VPN Concepts
- IKE
- Phase 1
- Phase 2
- Encryption Algorithms
- DH Groups
- PFS
- DPD
- Route-based VPN
- Policy-based VPN
- Dial-up VPN
- SSL VPN
- SSL VPN Overview
- Tunnel Mode
- Web Mode
- Portal
- Authentication
- Split Tunnel
- Full Tunnel
- Bookmarks

➡️ **مطالعه فصل:** [07-VPN.md](07-VPN.md)

---

## 08. SD-WAN

**فایل:** `08-SD-WAN.md`

این فصل معماری SD-WAN در FortiGate و نحوه مدیریت هوشمند چندین لینک WAN را بررسی می‌کند. در این بخش با انتخاب مسیر بر اساس کیفیت لینک، بررسی سلامت ارتباطات، Failover و Load Balancing آشنا خواهید شد.

**مباحث این فصل:**

- SD-WAN Architecture
- Members
- Zones
- SLA
- Performance SLA
- Health Check
- SD-WAN Rules
- Link Cost
- Failover
- Load Balancing
- Implicit Rule

➡️ **مطالعه فصل:** [08-SD-WAN.md](08-SD-WAN.md)

---

## 09. Security Profiles

**فایل:** `09-Security-Profiles.md`

این فصل به معرفی موتورهای امنیتی FortiGate می‌پردازد. در این بخش نحوه عملکرد قابلیت‌هایی مانند Antivirus، IPS، Web Filtering، Application Control و SSL Inspection بررسی می‌شود که نقش اصلی را در محافظت از شبکه در برابر تهدیدات ایفا می‌کنند.

**مباحث این فصل:**

- Antivirus
- Scan Mode
- Archive Scan
- Outbreak Prevention
- IPS
- Signature
- Sensors
- Protocol Decoders
- Rate Based Signatures
- Web Filter
- Category Filter
- URL Filter
- Static URL
- FortiGuard Categories
- DNS Filter
- Application Control
- SSL Inspection
- Certificate Inspection
- Deep Inspection
- Email Filter
- File Filter
- DLP
- ICAP

➡️ **مطالعه فصل:** [09-Security-Profiles.md](09-Security-Profiles.md)

---

## 10. High Availability

**فایل:** `10-High-Availability.md`

این فصل به بررسی معماری High Availability در FortiGate اختصاص دارد. در این بخش نحوه ایجاد کلاسترهای FortiGate، هماهنگی بین اعضا، همگام‌سازی اطلاعات، فرآیند Failover و جلوگیری از اختلال سرویس‌ها بررسی می‌شود.

**مباحث این فصل:**

- HA Overview
- Active Passive
- Active Active
- FGCP
- Heartbeat
- Session Pickup
- Override
- HA Priority
- Failover Process
- Split Brain
- Reserved Management Interface

➡️ **مطالعه فصل:** [10-High-Availability.md](10-High-Availability.md)

---
## 11. Logging & Monitoring

**فایل:** `11-Logging-Monitoring.md`

این فصل به مدیریت، ذخیره‌سازی و تحلیل Logها در FortiGate اختصاص دارد. در این بخش با انواع Log، روش‌های ذخیره‌سازی اطلاعات، اتصال به سیستم‌های مانیتورینگ، گزارش‌گیری و بررسی رخدادهای امنیتی آشنا خواهید شد.

**مباحث این فصل:**

- Log Types
- Local Logging
- Memory Logging
- Disk Logging
- FortiAnalyzer
- FortiCloud
- Syslog
- SNMP
- Automation Event
- Alert Email
- Report

➡️ **مطالعه فصل:** [11-Logging-Monitoring.md](11-Logging-Monitoring.md)

---

## 12. Security Fabric

**فایل:** `12-Security-Fabric.md`

این فصل معماری Security Fabric در اکوسیستم Fortinet را بررسی می‌کند. در این بخش نحوه ارتباط و هماهنگی بین محصولات مختلف Fortinet، ایجاد دید یکپارچه امنیتی، اتصال تجهیزات و استفاده از قابلیت‌های خودکارسازی بررسی می‌شود.

**مباحث این فصل:**

- Security Fabric Overview
- Fabric Connectors
- Fabric Devices
- Fabric Topology
- Fabric Rating
- EMS Integration
- Automation

➡️ **مطالعه فصل:** [12-Security-Fabric.md](12-Security-Fabric.md)

---

## 13. Switching

**فایل:** `13-Switching.md`

این فصل قابلیت‌های Switching در اکوسیستم Fortinet را بررسی می‌کند. در این بخش با مفاهیم شبکه لایه دوم، مدیریت VLAN، اتصال FortiSwitch به FortiGate، پروتکل‌های کنترلی و تکنیک‌های افزایش کارایی لینک‌ها آشنا خواهید شد.

**مباحث این فصل:**

- VLAN
- FortiSwitch
- FortiLink
- Hardware Switch
- Software Switch
- LACP
- LLDP
- STP

➡️ **مطالعه فصل:** [13-Switching.md](13-Switching.md)

---

## 14. Wireless

**فایل:** `14-Wireless.md`

این فصل به مدیریت شبکه‌های Wireless با استفاده از Fortinet اختصاص دارد. در این بخش معماری FortiAP، کنترلر Wireless داخلی FortiGate، ایجاد SSID، روش‌های امنیتی و مدیریت تجهیزات بی‌سیم بررسی می‌شود.

**مباحث این فصل:**

- FortiAP
- SSID
- Security Modes
- WPA2
- WPA3
- CAPWAP
- Wireless Controller
- Rogue AP Detection

➡️ **مطالعه فصل:** [14-Wireless.md](14-Wireless.md)

---

## 15. Web Proxy

**فایل:** `15-Web-Proxy.md`

این فصل قابلیت‌های Web Proxy در FortiGate را بررسی می‌کند. در این بخش نحوه کنترل دسترسی کاربران به اینترنت، مدیریت Proxy Policyها، احراز هویت کاربران و استفاده از PAC File برای هدایت ترافیک مرورگرها آموزش داده می‌شود.

**مباحث این فصل:**

- Explicit Proxy
- Transparent Proxy
- Proxy Policies
- PAC File
- Authentication

➡️ **مطالعه فصل:** [15-Web-Proxy.md](15-Web-Proxy.md)

---
## 16. Certificates

**فایل:** `16-Certificates.md`

این فصل به بررسی مفاهیم Certificate و زیرساخت کلید عمومی (PKI) در FortiGate اختصاص دارد. در این بخش نحوه استفاده از گواهی‌های دیجیتال برای احراز هویت، رمزنگاری ارتباطات، SSL Inspection و مدیریت Certificateها بررسی می‌شود.

**مباحث این فصل:**

- PKI
- CA
- CSR
- Local Certificate
- Remote Certificate
- Certificate Inspection

➡️ **مطالعه فصل:** [16-Certificates.md](16-Certificates.md)

---

## 17. VDOM

**فایل:** `17-VDOM.md`

این فصل قابلیت Virtual Domain یا VDOM در FortiGate را بررسی می‌کند. در این بخش نحوه تقسیم یک FortiGate فیزیکی به چند Firewall مستقل، مدیریت منابع، ارتباط بین VDOMها و استفاده از VDOM در محیط‌های سازمانی و چندمستاجری آموزش داده می‌شود.

**مباحث این فصل:**

- VDOM Overview
- NAT Mode
- Transparent Mode
- Inter-VDOM Link
- Management VDOM
- Resource Allocation

➡️ **مطالعه فصل:** [17-VDOM.md](17-VDOM.md)

---

## 18. Traffic Shaping & QoS

**فایل:** `18-Traffic-Shaping-QoS.md`

این فصل به معرفی مکانیزم‌های مدیریت پهنای باند (Traffic Shaping) و کیفیت سرویس (QoS) در FortiGate می‌پردازد. در این بخش روش‌های کنترل مصرف پهنای باند، اولویت‌بندی ترافیک، مدیریت کیفیت سرویس و بهینه‌سازی استفاده از منابع شبکه بررسی می‌شود.

**مباحث این فصل:**

- Shared Shaper
- Per-IP Shaper
- QoS
- DSCP
- Priority
- Bandwidth Control

➡️ **مطالعه فصل:** [18-Traffic-Shaping-QoS.md](18-Traffic-Shaping-QoS.md)

---

## 19. Automation

**فایل:** `19-Automation.md`

این فصل قابلیت‌های Automation در FortiGate را بررسی می‌کند. در این بخش نحوه ایجاد فرآیندهای خودکار برای واکنش به رخدادهای امنیتی، اجرای Scriptها، ارسال اعلان‌ها و اتصال FortiGate به سرویس‌های خارجی آموزش داده می‌شود.

**مباحث این فصل:**

- Automation Stitch
- Trigger
- Action
- CLI Script
- Webhook
- Slack Notification
- Email Notification

➡️ **مطالعه فصل:** [19-Automation.md](19-Automation.md)

