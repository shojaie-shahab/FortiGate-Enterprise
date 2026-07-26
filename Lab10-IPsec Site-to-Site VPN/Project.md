
# تسک 1 - Configuring IPsec Phase 1



# هدف

در این Task، Phase 1 مربوط به IPsec Site-to-Site VPN بین دو FortiGate ایجاد می‌شود.

ا Phase 1 اولین مرحله برقراری VPN است و وظیفه آن ایجاد یک کانال امن برای مذاکره کلیدهای رمزنگاری (Key Exchange) و احراز هویت دو طرف VPN است.

در پایان این Task:

- یک IPsec Tunnel ایجاد می‌شود.
- احراز هویت دو FortiGate انجام می‌شود.
- تنظیمات رمزنگاری Phase 1 تکمیل خواهد شد.



# تنظیمات مورد نیاز

در این سناریو از تنظیمات زیر استفاده می‌کنیم.

HQ FortiGate

WAN IP

```
192.168.100.10
```

Branch FortiGate

WAN IP

```
192.168.100.20
```

نام Tunnel

```
HQ-BRANCH-VPN
```

Pre-Shared Key

```
FortiVPN@123
```

IKE Version

```
IKEv2
```



# پیاده‌سازی در GUI

از منوی سمت چپ وارد شوید.

```
VPN

↓

IPsec Wizard
```

یا در بعضی نسخه‌های FortiOS:

```
VPN

↓

IPsec Tunnels

↓

Create New

↓

IPsec Tunnel
```

---

# انتخاب Template

در اولین صفحه Wizard گزینه زیر را انتخاب کنید.

```
Custom
```

### توضیح

گزینه Custom اجازه می‌دهد تمامی تنظیمات Phase 1 و Phase 2 را به صورت دستی انجام دهیم. این روش برای یادگیری و همچنین محیط‌های سازمانی مناسب‌تر است.

---

# Tunnel Name

قسمت

```
Name
```

را به صورت زیر وارد کنید.

```
HQ-BRANCH-VPN
```

### توضیح

این نام صرفاً برای شناسایی Tunnel در FortiGate استفاده می‌شود و روی عملکرد VPN تأثیری ندارد.

---

# Remote Gateway

قسمت

```
Remote Gateway
```

را روی

```
Static IP Address
```

قرار دهید.

سپس مقدار زیر را وارد کنید.

```
192.168.100.20
```

### توضیح

چون IP سمت Branch ثابت است، از Static IP استفاده می‌کنیم.

اگر سمت مقابل IP ثابتی نداشت، باید از Dynamic DNS یا Dialup VPN استفاده می‌شد.

---

# Interface

قسمت

```
Interface
```

را روی Interface متصل به WAN قرار دهید.

```
port1
```

### توضیح

تمام Packetهای IPsec از این Interface ارسال خواهند شد.

---

# Authentication Method

قسمت

```
Authentication Method
```

را روی

```
Pre-shared Key
```

قرار دهید.

سپس مقدار زیر را وارد کنید.

```
FortiVPN@123
```

### توضیح

این کلید باید در هر دو FortiGate کاملاً یکسان باشد.

در صورت متفاوت بودن PSK، Phase 1 هرگز برقرار نخواهد شد.

---

# IKE Version

قسمت

```
IKE Version
```

را روی

```
Version 2
```

قرار دهید.

### توضیح

IKEv2 نسبت به IKEv1:

- امنیت بالاتر
- سرعت بیشتر
- پایداری بهتر
- پشتیبانی بهتر از NAT Traversal

دارد و در اکثر شبکه‌های جدید استفاده می‌شود.

---

# Mode

قسمت

```
Mode
```

را روی

```
Main
```

قرار دهید.

### توضیح

ا Main Mode اطلاعات احراز هویت را به صورت رمزنگاری شده ارسال می‌کند و امنیت بیشتری نسبت به Aggressive Mode دارد.

---

# NAT Traversal (NAT-T)

گزینه

```
NAT Traversal
```

را روی

```
Enable
```

قرار دهید.

### توضیح

اگر یکی از دو FortiGate پشت NAT قرار داشته باشد، NAT-T باعث عبور صحیح Packetهای IPsec می‌شود.

فعال بودن آن حتی در این Lab نیز توصیه می‌شود.

---

# Dead Peer Detection (DPD)

قسمت

```
Dead Peer Detection
```

را روی

```
On Idle
```

قرار دهید.

### توضیح

ا DPD وضعیت طرف مقابل را بررسی می‌کند.

در صورتی که ارتباط قطع شود، Tunnel مجدداً برقرار خواهد شد.

---

# Encryption Proposal

قسمت

```
Encryption
```

را روی

```
AES256
```

قرار دهید.

قسمت

```
Authentication
```

را روی

```
SHA256
```

قرار دهید.

### توضیح

این ترکیب یکی از رایج‌ترین Proposalهای سازمانی است و امنیت بالایی دارد.

---

# Diffie-Hellman Group

قسمت

```
DH Group
```

را روی

```
14
```

قرار دهید.

### توضیح

ا DH Group وظیفه تولید کلیدهای رمزنگاری اولیه را بر عهده دارد.

ا Group 14 یکی از متداول‌ترین گزینه‌ها در شبکه‌های سازمانی است.

---

# Key Lifetime

قسمت

```
Key Lifetime
```

را روی مقدار پیش‌فرض

```
28800 Seconds
```

قرار دهید.

### توضیح

پس از پایان این زمان، کلیدهای Phase 1 دوباره تولید خواهند شد.

---

# ذخیره تنظیمات

روی

```
OK
```

یا

```
Save
```

کلیک کنید.

---

# پیاده‌سازی از طریق CLI

روی HQ FortiGate دستورهای زیر را اجرا کنید.

```bash
config vpn ipsec phase1-interface

edit HQ-BRANCH-VPN

set interface port1

set remote-gw 192.168.100.20

set ike-version 2

set peertype any

set proposal aes256-sha256

set dhgrp 14

set psksecret FortiVPN@123

set nattraversal enable

set dpd on-idle

next

end
```

---

# بررسی Tunnel

برای مشاهده تنظیمات Phase 1:

```bash
show vpn ipsec phase1-interface
```

---

برای بررسی وضعیت Tunnel:

```bash
diagnose vpn ike gateway list
```

در این مرحله طبیعی است که Tunnel هنوز Up نباشد، زیرا Phase 2 و تنظیمات سمت مقابل هنوز ایجاد نشده‌اند.

---

# نتیجه

در این Task تنظیمات Phase 1 روی FortiGate HQ ایجاد شد.

در Task بعدی همین تنظیمات روی FortiGate Branch اعمال می‌شود و سپس Phase 2 را پیکربندی خواهیم کرد تا Tunnel آماده برقراری ارتباط شود.



<br><br>



# تسک 2 - Configuring IPsec Phase 2

# هدف

در این Task تنظیمات Phase 2 مربوط به IPsec Site-to-Site VPN انجام می‌شود.

ا Phase 2 مشخص می‌کند:

- کدام شبکه‌ها از داخل Tunnel عبور کنند.
- از چه الگوریتم رمزنگاری برای انتقال داده‌ها استفاده شود.
- آیا Perfect Forward Secrecy فعال باشد یا خیر.

در پایان این Task:

- ا Local Network مشخص می‌شود.
- اRemote Network مشخص می‌شود.
- ا Security Association مربوط به انتقال داده ایجاد خواهد شد.



# تنظیمات مورد نیاز

HQ LAN

```
192.168.10.0/24
```

Branch LAN

```
192.168.20.0/24
```

Proposal

```
AES256-SHA256
```

PFS

```
Enable
```

DH Group

```
14
```

Lifetime

```
3600 Seconds
```

---

# تنظیم Phase 2 روی FortiGate HQ

از منوی زیر وارد شوید.

```
VPN

↓

IPsec Tunnels

↓

HQ-BRANCH-VPN

↓

Edit
```

به قسمت

```
Phase 2 Selectors
```

بروید.

---

# Name

نام Phase2 را به صورت زیر قرار دهید.

```
P2-HQ-BRANCH
```

---

# Local Address

قسمت

```
Local Address
```

را روی

```
Subnet
```

قرار دهید.

مقدار:

```
192.168.10.0/24
```

### توضیح

این همان شبکه داخلی HQ است.

تمام Packetهایی که مقصد آن‌ها Branch باشد از این شبکه وارد Tunnel خواهند شد.

---

# Remote Address

قسمت

```
Remote Address
```

را روی

```
Subnet
```

قرار دهید.

مقدار:

```
192.168.20.0/24
```

### توضیح

این شبکه داخلی شعبه است.

---

# Encryption Proposal

قسمت

```
Encryption
```

را روی

```
AES256
```

قرار دهید.

قسمت

```
Authentication
```

را روی

```
SHA256
```

قرار دهید.

---

# Enable PFS

گزینه

```
Enable Perfect Forward Secrecy (PFS)
```

را فعال کنید.

سپس

```
DH Group

↓

14
```

را انتخاب کنید.

### توضیح

ا PFS باعث می‌شود برای هر ارتباط، کلید رمزنگاری جدید تولید شود و امنیت VPN افزایش پیدا کند.

---

# Key Lifetime

قسمت

```
Key Lifetime
```

را روی

```
3600
```

ثانیه قرار دهید.

---

# ذخیره تنظیمات

روی

```
OK
```

کلیک کنید.

---

# تنظیم Phase 2 روی FortiGate Branch

همان مراحل را انجام دهید.

تنها تفاوت:

Local Address

```
192.168.20.0/24
```

Remote Address

```
192.168.10.0/24
```

خواهد بود.

بقیه تنظیمات دقیقاً مشابه HQ هستند.

---

# پیاده‌سازی HQ از طریق CLI

```bash
config vpn ipsec phase2-interface

edit P2-HQ-BRANCH

set phase1name HQ-BRANCH-VPN

set proposal aes256-sha256

set pfs enable

set dhgrp 14

set src-subnet 192.168.10.0 255.255.255.0

set dst-subnet 192.168.20.0 255.255.255.0

set keylifeseconds 3600

next

end
```

---

# پیاده‌سازی Branch از طریق CLI

```bash
config vpn ipsec phase2-interface

edit P2-BRANCH-HQ

set phase1name HQ-BRANCH-VPN

set proposal aes256-sha256

set pfs enable

set dhgrp 14

set src-subnet 192.168.20.0 255.255.255.0

set dst-subnet 192.168.10.0 255.255.255.0

set keylifeseconds 3600

next

end
```

---

# بررسی تنظیمات

نمایش Phase 2

```bash
show vpn ipsec phase2-interface
```

---

بررسی Security Association

```bash
diagnose vpn tunnel list
```

در این مرحله ممکن است Tunnel هنوز Down باشد، زیرا هنوز:

- Static Route
- Firewall Policy

ایجاد نشده‌اند.

این کاملاً طبیعی است.

---

# نکات مهم

برای اینکه Phase 2 با موفقیت برقرار شود، موارد زیر باید در هر دو FortiGate یکسان باشند:

- Proposal
- PFS
- DH Group
- Lifetime

همچنین:

ا Local و Remote Subnet باید برعکس یکدیگر تعریف شوند.

مثال:

HQ

```
Local

192.168.10.0/24

Remote

192.168.20.0/24
```

Branch

```
Local

192.168.20.0/24

Remote

192.168.10.0/24
```

---

# نتیجه

در این Task تنظیمات Phase 2 روی هر دو FortiGate انجام شد.

اکنون Tunnel از نظر رمزنگاری آماده است، اما هنوز هیچ ترافیکی از داخل آن عبور نخواهد کرد.

در Task بعدی، **Static Route** و سپس **Firewall Policy** ایجاد می‌شود تا ارتباط بین دو شبکه برقرار گردد.


<br><br>

# تسک 3 - Configuring Static Routes for the IPsec Tunnel



# هدف

در این Task مسیرهای (Static Route) مورد نیاز برای عبور ترافیک از داخل Tunnel ایجاد می‌شوند.

پس از ایجاد Tunnel، FortiGate هنوز نمی‌داند Packetهای مربوط به شبکه مقصد را باید از داخل VPN ارسال کند.

به همین دلیل باید مسیر مناسب به صورت دستی ایجاد شود.

در پایان این Task:

- ا Static Route روی FortiGate HQ ایجاد خواهد شد.
- ا Static Route روی FortiGate Branch ایجاد خواهد شد.
- جدول Routing بررسی خواهد شد.


# چرا Static Route لازم است؟

ا Tunnel فقط یک ارتباط امن ایجاد می‌کند.

اما FortiGate همچنان باید تصمیم بگیرد که Packetهای مقصد را از کدام Interface ارسال کند.

مثلاً اگر یک Client در HQ بخواهد به شبکه Branch متصل شود، FortiGate باید بداند:

```
Destination:

192.168.20.0/24

↓

Send Through

HQ-BRANCH-VPN
```

اگر این Route وجود نداشته باشد، Packetها از WAN ارسال می‌شوند و VPN هرگز استفاده نخواهد شد.

---

# ایجاد Static Route روی HQ

از منوی زیر وارد شوید.

```
Network

↓

Static Routes

↓

Create New
```

---

# Destination

در قسمت

```
Destination
```

مقدار زیر را وارد کنید.

```
192.168.20.0/24
```

### توضیح

این شبکه داخلی شعبه است.

---

# Interface

قسمت

```
Interface
```

را روی Tunnel ایجاد شده قرار دهید.

```
HQ-BRANCH-VPN
```

### توضیح

به FortiGate می‌گوییم تمام Packetهای مربوط به شبکه Branch از داخل Tunnel عبور کنند.

---

# Gateway

در Route-based VPN نیازی به وارد کردن Gateway نیست.

این قسمت را خالی بگذارید.

---

# Distance

مقدار پیش‌فرض

```
10
```

را تغییر ندهید.

### توضیح

ا Administrative Distance اولویت Route را مشخص می‌کند.

عدد کمتر یعنی اولویت بیشتر.

---

# ذخیره Route

روی

```
OK
```

کلیک کنید.

---

# ایجاد Static Route روی Branch

همان مراحل را انجام دهید.

تنها تفاوت:

Destination

```
192.168.10.0/24
```

Interface

```
HQ-BRANCH-VPN
```

---

# پیاده‌سازی HQ از طریق CLI

```bash
config router static

edit 1

set dst 192.168.20.0 255.255.255.0

set device HQ-BRANCH-VPN

next

end
```

---

# پیاده‌سازی Branch از طریق CLI

```bash
config router static

edit 1

set dst 192.168.10.0 255.255.255.0

set device HQ-BRANCH-VPN

next

end
```

---

# بررسی جدول Routing

برای مشاهده Routeها:

```bash
get router info routing-table all
```

یا

```bash
get router info routing-table details
```

---

نمونه خروجی

```
S

192.168.20.0/24

via

HQ-BRANCH-VPN
```

حرف

```
S
```

به معنی

```
Static Route
```

است.

---

# بررسی Route خاص

```bash
get router info routing-table details 192.168.20.0
```

یا

```bash
get router info routing-table details 192.168.10.0
```

---

# نکات مهم

در HQ:

```
Destination

192.168.20.0/24
```

---

در Branch:

```
Destination

192.168.10.0/24
```

---

هیچ Gateway برای این Routeها تعریف نکنید.

ا Interface باید همان Interface مربوط به Tunnel باشد.

---

# خطاهای رایج

## انتخاب اشتباه Interface

اگر به جای Tunnel، Interface WAN انتخاب شود:

ا Packetها وارد VPN نخواهند شد.

---

## تعریف اشتباه Destination

اگر Subnet اشتباه وارد شود:

ا FortiGate هرگز Packetها را وارد Tunnel نمی‌کند.

---

## فراموش کردن Route

یکی از رایج‌ترین مشکلات Site-to-Site VPN همین مورد است.

ا Tunnel ممکن است کاملاً Up باشد، اما هیچ ارتباطی بین دو سایت برقرار نشود.

---

# نتیجه

در این Task مسیرهای لازم برای هدایت ترافیک به داخل Tunnel ایجاد شدند.

اکنون FortiGate می‌داند که Packetهای مربوط به شبکه مقابل باید از طریق VPN ارسال شوند.

در Task بعدی، Firewall Policyهای لازم ایجاد می‌شوند تا عبور ترافیک از Tunnel مجاز شود.


<br><br>


# تسک 4 - Configuring Firewall Policies



# هدف

در این Task، Firewall Policyهای مورد نیاز برای عبور ترافیک از داخل IPsec Tunnel ایجاد می‌شوند.

پس از ایجاد Tunnel و Static Route، هنوز FortiGate Packetها را Drop می‌کند، زیرا هیچ Policyای برای اجازه عبور ترافیک وجود ندارد.

در پایان این Task:

- ا Policy از HQ به Branch ایجاد خواهد شد.
- ا Policy از Branch به HQ ایجاد خواهد شد.
- ا NAT برای VPN غیرفعال خواهد شد.

---

# چرا Firewall Policy لازم است؟

ا FortiGate بر اساس Firewall Policy تصمیم می‌گیرد که آیا یک Packet اجازه عبور دارد یا خیر.

اگر هیچ Policyای وجود نداشته باشد:

```
Packet

↓

FortiGate

↓

Denied
```

بنابراین حتی اگر Tunnel کاملاً برقرار باشد، بدون Firewall Policy هیچ ارتباطی برقرار نخواهد شد.

---

# ایجاد Policy روی FortiGate HQ

از منوی زیر وارد شوید.

```
Policy & Objects

↓

Firewall Policy

↓

Create New
```

---

# Name

در قسمت

```
Name
```

مقدار زیر را وارد کنید.

```
HQ-to-BRANCH-VPN
```

---

# Incoming Interface

قسمت

```
Incoming Interface
```

را روی

```
port2
```

قرار دهید.

### توضیح

شبکه داخلی HQ از طریق Interface

```
port2
```

به FortiGate متصل است.

---

# Outgoing Interface

قسمت

```
Outgoing Interface
```

را روی Tunnel انتخاب کنید.

```
HQ-BRANCH-VPN
```

---

# Source

قسمت

```
Source
```

را روی

```
192.168.10.0/24
```

یا Address Object مربوط به شبکه HQ قرار دهید.

---

# Destination

قسمت

```
Destination
```

را روی

```
192.168.20.0/24
```

قرار دهید.

---

# Schedule

```
Always
```

---

# Service

```
ALL
```

در محیط عملی بهتر است فقط سرویس‌های مورد نیاز را مجاز کنید، اما برای این Lab از

```
ALL
```

استفاده می‌کنیم.

---

# Action

```
Accept
```

---

# NAT

گزینه

```
NAT
```

را **غیرفعال (Disable)** کنید.

### توضیح

یکی از رایج‌ترین اشتباهات در IPsec VPN فعال بودن NAT است.

اگر NAT فعال باشد، آدرس مبدأ تغییر می‌کند و ارتباط بین دو سایت به درستی برقرار نخواهد شد.

در ارتباط Site-to-Site معمولاً NAT استفاده نمی‌شود.

---

# ذخیره Policy

روی

```
OK
```

کلیک کنید.

---

# ایجاد Policy روی FortiGate Branch

همان مراحل را انجام دهید.

تنها تفاوت:

Name

```
BRANCH-to-HQ-VPN
```

Incoming Interface

```
port2
```

Outgoing Interface

```
HQ-BRANCH-VPN
```

Source

```
192.168.20.0/24
```

Destination

```
192.168.10.0/24
```

NAT

```
Disable
```

---

# پیاده‌سازی HQ از طریق CLI

```bash
config firewall policy

edit 1

set name HQ-to-BRANCH-VPN

set srcintf port2

set dstintf HQ-BRANCH-VPN

set srcaddr all

set dstaddr all

set action accept

set schedule always

set service ALL

set nat disable

next

end
```

---

# پیاده‌سازی Branch از طریق CLI

```bash
config firewall policy

edit 1

set name BRANCH-to-HQ-VPN

set srcintf port2

set dstintf HQ-BRANCH-VPN

set srcaddr all

set dstaddr all

set action accept

set schedule always

set service ALL

set nat disable

next

end
```

---

# بررسی Policyها

برای مشاهده Policyها:

```bash
show firewall policy
```

---

برای مشاهده خلاصه Policyها:

```bash
get firewall policy
```

---

# بررسی NAT

برای اطمینان از غیرفعال بودن NAT:

```bash
show firewall policy
```

باید مشاهده کنید:

```bash
set nat disable
```



# خطاهای رایج

## فعال بودن NAT

اگر NAT فعال باشد:

- ا 
Tunnel ممکن است Up باشد.
- اما ارتباط بین دو LAN برقرار نخواهد شد.

---

## انتخاب اشتباه Interface

ا Incoming Interface باید شبکه داخلی باشد.

ا Outgoing Interface باید Interface مربوط به Tunnel باشد.

برعکس انتخاب کردن آن‌ها باعث Drop شدن Packetها می‌شود.

---

## نبود Policy در یکی از دو سمت

ا VPN همیشه دوطرفه است.

اگر فقط روی HQ Policy ایجاد شود و روی Branch وجود نداشته باشد، ارتباط کامل برقرار نخواهد شد.

---

# نتیجه

در این Task، Firewall Policyهای مورد نیاز برای عبور ترافیک بین HQ و Branch ایجاد شدند.

همچنین NAT برای ترافیک VPN غیرفعال شد تا آدرس‌های واقعی دو شبکه در داخل Tunnel حفظ شوند.

اکنون تمامی تنظیمات اصلی Site-to-Site VPN تکمیل شده است.

در Task بعدی، Tunnel را بررسی کرده، ارتباط بین دو سایت را تست می‌کنیم و وضعیت Security Association و VPN را مشاهده خواهیم کرد.


<br><br>



# تسک 5 - Testing and Verifying the Site-to-Site VPN

---

# هدف

در این Task صحت عملکرد Site-to-Site VPN بررسی می‌شود.

در پایان این Task:

- وضعیت Tunnel بررسی خواهد شد.
- ارتباط بین دو سایت تست خواهد شد.
- وضعیت Security Association (SA) بررسی می‌شود.
- صحت عبور ترافیک از داخل Tunnel تأیید خواهد شد.

---

# بررسی وضعیت Tunnel در GUI

از منوی زیر وارد شوید.

```
VPN

↓

IPsec Tunnels
```

در این قسمت Tunnel ایجاد شده باید نمایش داده شود.

نمونه:

```
HQ-BRANCH-VPN

Status

↓

Up
```

اگر وضعیت Down بود نگران نباشید، تا زمانی که ترافیکی از داخل Tunnel عبور نکند، ممکن است Tunnel برقرار نشود.

---

# ایجاد اولین ترافیک

از کامپیوتر HQ دستور زیر را اجرا کنید.

```
ping 192.168.20.100
```

یا اگر Client در اختیار ندارید، از خود FortiGate استفاده کنید.

روی HQ:

```bash
execute ping-options source 192.168.10.1

execute ping 192.168.20.1
```

---

روی Branch نیز می‌توانید تست کنید.

```bash
execute ping-options source 192.168.20.1

execute ping 192.168.10.1
```

---

# بررسی وضعیت Tunnel از طریق CLI

روی هر دو FortiGate:

```bash
get vpn ipsec tunnel summary
```

نمونه خروجی:

```
VPN Tunnel Summary

------------------

HQ-BRANCH-VPN

Status:

Up
```

---

# مشاهده اطلاعات کامل Tunnel

```bash
diagnose vpn tunnel list
```

این دستور اطلاعات زیر را نمایش می‌دهد:

- نام Tunnel
- وضعیت Tunnel
- Phase 1
- Phase 2
- Proposal
- Encryption
- Bytes Sent
- Bytes Received

---

# بررسی IKE Security Association

```bash
diagnose vpn ike gateway list
```

نمونه خروجی:

```
IKE SA

State:

Established
```

اگر عبارت

```
Established
```

نمایش داده شود، Phase 1 با موفقیت برقرار شده است.

---

# بررسی IPsec Security Association

```bash
diagnose vpn tunnel list
```

در خروجی به بخش زیر توجه کنید.

```
enc:

#####

dec:

#####
```

### توضیح

enc

تعداد Packetهای رمزنگاری شده

dec

تعداد Packetهای رمزگشایی شده

اگر این اعداد افزایش پیدا کنند، یعنی Packetها از داخل Tunnel عبور می‌کنند.

---

# بررسی Routing Table

```bash
get router info routing-table all
```

باید Route مربوط به شبکه مقصد مشاهده شود.

مثال:

```
192.168.20.0/24

↓

HQ-BRANCH-VPN
```

---

# بررسی Session

```bash
diagnose sys session list
```

در زمان Ping یا ارتباط بین دو سایت، Sessionهای مربوط به VPN در این قسمت نمایش داده می‌شوند.

---

# تست ارتباط بین دو LAN

از HQ-PC:

```
ping 192.168.20.100
```

---

از Branch-PC:

```
ping 192.168.10.100
```

اگر پاسخ دریافت شد، Tunnel به درستی کار می‌کند.

---

# بررسی Counterها

در زمان ارسال Ping، دوباره دستور زیر را اجرا کنید.

```bash
diagnose vpn tunnel list
```

اعداد زیر باید افزایش پیدا کنند.

```
enc

↓

Increasing


dec

↓

Increasing
```

اگر این اعداد صفر باقی بمانند، ترافیکی وارد Tunnel نشده است.

---

# بررسی Firewall Policy

از منوی:

```
Policy & Objects

↓

Firewall Policy
```

Policy مربوط به VPN را باز کنید.

در قسمت

```
Hit Count
```

باید تعداد برخورد به Policy افزایش پیدا کند.

این نشان می‌دهد که ترافیک از این Policy عبور کرده است.

---

# بررسی وضعیت Interface Tunnel

```bash
get system interface
```

یا

```bash
show system interface
```

باید Interface مربوط به Tunnel در وضعیت فعال باشد.

---

# بررسی از Dashboard

از منوی:

```
Dashboard

↓

Network

↓

IPsec Monitor
```

می‌توانید موارد زیر را مشاهده کنید:

- وضعیت Tunnel
- مدت زمان اتصال
- حجم داده ارسال شده
- حجم داده دریافت شده

---

# نکات مهم

اگر Tunnel Up شد اما Ping انجام نشد، معمولاً یکی از موارد زیر مشکل دارد:

- Static Route
- Firewall Policy
- Local یا Remote Subnet
- NAT
- Gateway سیستم‌های Client

---

اگر Tunnel حتی Up هم نشد، ابتدا موارد زیر را بررسی کنید:

- Pre-Shared Key
- Proposal
- DH Group
- IKE Version
- Remote Gateway

---

# نتیجه

در این Task عملکرد Site-to-Site VPN بررسی شد.

همچنین:

- وضعیت Tunnel
- ا Security Association
- مسیرهای Routing
- ا Sessionها
- عبور Packetها

با استفاده از دستورات CLI و محیط گرافیکی FortiGate بررسی شدند.
