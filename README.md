# FortiGate-Enterprise


## لابراتوار پیشنهادی

* ۱ عدد FortiGate VM
* ۱ عدد Windows Server
* ۲ عدد Windows Client
* ۱ عدد Kali Linux
* ۱ عدد Ubuntu Server
* در صورت امکان یک FortiAnalyzer VM

حداقل ۴ شبکه ایجاد کن:

* WAN
* LAN
* DMZ
* Guest



# سناریو ۱: نصب و راه‌اندازی اولیه

### هدف

آشنایی کامل با GUI و CLI

### موارد آموزشی

* نصب FortiGate VM
* Interface
* Static Route
* Default Gateway
* DNS
* Admin
* Backup و Restore
* Firmware
* Time/NTP

### توپولوژی

```
Internet
     |
FortiGate
     |
 Windows Client
```

### در پایان باید بتوانی

* به اینترنت وصل شوی.
* از CLI و GUI کار کنی.
* Backup بگیری.
* Firmware را ارتقا دهی.



# سناریو ۲: Firewall Policy

### هدف

مهم‌ترین بخش NSE4

### یاد می‌گیری

* Policy
* NAT
* VIP
* Schedule
* Service
* Address Object
* Address Group

### توپولوژی

```
LAN ---- FortiGate ----- WAN
```

تمرین

* فقط HTTP مجاز باشد.
* HTTPS مسدود شود.
* فقط یک IP اینترنت داشته باشد.
* اینترنت فقط در ساعات اداری فعال باشد.



# سناریو ۳: NAT و VIP

### هدف

Port Forward

### توپولوژی

```
Internet
      |
FortiGate
      |
 Web Server
```

پیاده‌سازی

* Web Server
* SSH
* RDP
* Static NAT
* VIP

تمرین

از اینترنت وارد وب‌سرور شو.



# سناریو ۴: User Authentication

### یاد می‌گیری

* Local User
* LDAP
* RADIUS
* FSSO
* Captive Portal

تمرین

* اینترنت بدون Login قطع باشد.
* کاربران بعد از Login اینترنت داشته باشند.



# سناریو ۵: SSL VPN

از محبوب‌ترین بخش‌های NSE4

### توپولوژی

```
Laptop
   |
Internet
   |
FortiGate
   |
LAN
```

یاد می‌گیری

* SSL VPN
* Tunnel
* Web Mode
* Split Tunnel
* Full Tunnel
* MFA

تمرین

از بیرون وارد شبکه شو.



# سناریو ۶: IPS و Antivirus

### راه‌اندازی

* IPS
* AV
* Application Control
* Web Filter
* DNS Filter

تمرین

* حمله Nmap
* حمله SQL Injection
* دانلود فایل آلوده

ببین FortiGate چه رفتاری دارد.

---

# سناریو ۷: Routing

### یادگیری

* Static Route
* Policy Route
* ECMP
* SD-WAN
* OSPF
* BGP (مقدماتی)

توپولوژی

```
ISP1
    \
     FortiGate
    /
ISP2
```

تمرین

Failover انجام بده.



# سناریو ۸: High Availability

### دو FortiGate

```
FGT1
   ||
FGT2
```

یادگیری

* Active-Passive
* Heartbeat
* Sync
* Failover

تمرین

یکی را خاموش کن.

ببین شبکه قطع نشود.



# سناریو ۹: Logging

یادگیری

* Local Log
* Syslog
* FortiAnalyzer
* Event Log
* Traffic Log

تمرین

تمام رخدادها را تحلیل کن.


# سناریو ۱۰: SD-WAN

دو اینترنت

```
ISP1
   \
    FortiGate
   /
ISP2
```

یادگیری

* SLA
* Health Check
* Priority
* Load Balance

تمرین

اگر ISP1 قطع شد، ترافیک از ISP2 عبور کند.



# سناریو ۱۱: Site-to-Site IPsec VPN

```
Branch -------- Internet -------- HQ
```

یادگیری

* Phase1
* Phase2
* Route
* Policy

تمرین

دو شبکه همدیگر را Ping کنند.



# سناریو ۱۲: پروژه نهایی (ترکیبی)

این سناریو تقریباً همه مباحث NSE4 را پوشش می‌دهد.

```
                 Internet
                     |
          ISP1                 ISP2
             \                 /
              \               /
             +----------------+
             |   FortiGate    |
             +----------------+
          /         |          \
       LAN        DMZ        Guest
        |           |           |
   Windows PC   Web Server   WiFi Users
        |
   Active Directory
```

در این پروژه باید پیاده‌سازی کنی:

* Interface
* VLAN
* DHCP
* DNS
* NAT
* VIP
* Firewall Policy
* Static Route
* SD-WAN
* SSL VPN
* IPsec VPN
* IPS
* Antivirus
* Web Filter
* Application Control
* User Authentication
* LDAP
* Logging
* Backup
* HA 
