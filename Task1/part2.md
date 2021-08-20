# Part 2
## Content
---
1. <a href="#1">SSL and related terms and issues</a>
2. <a href="#2">What is a domain?</a>
3. <a href="#3">What is DNS? A number of DNS records.</a>
4. <a href="#4">What is hosting, vps, server?</a>
5. <a href="#5">What is reverse proxy, working principle?</a>
6. <a href="#6">Comparison between Nginx and Apache?</a>
---
<div id="1"></div>

## 1. SSL and related terms

### 1.1 Definition
> SSL stands for Secure Sockets Layer

> It's the standard technology for keeping an internet connection secure and safeguarding any sensitive data that is being sent between two systems, preventing criminals from reading and modifying any information transferred, including potential personal details.

### 1.2 Related term
1. Domain Validation (DV SSL).
> Domain Validation SSL certificates are the most basic of the three types of SSL/TLS certificates.

> Domain Validation takes just a single step.

> You only need to prove that you have ownership over the domain(s) that you’re requesting on the SSL certificate.
2. Organization Validation (OV SSL).
> Organization Validation (OV) SSL certificates provide an extra level of online trust by authenticating the business identity and legitimacy.

> Organizations must prove it owns the domain name it wishes to secure and confirm that it is a legally registered business.

3. Extended Validation (EV SSL).
> is the highest form of SSL Certificate on the market.

>During verification of an EV SSL Certificate, the owner of the website passes a thorough and globally standardized identity verification process to prove exclusive rights to use a domain, confirm its legal, operational and physical existence, and prove the entity has authorized the issuance of the certificate.
4. Subject Alternative Names (SANs SSL).
> Subject alternative name is a structured way to indicate all of the domain names and IP addresses that are secured by the certificate. Included on the short list of items that are considered a SAN are subdomains and IP addresses.
5. Wildcard SSL Certificate (Wildcard SSL).
> A SSL/TLS Wildcard certificate is a single certificate with a wildcard character (*) in the domain name field. This allows the certificate to secure multiple sub domain names (hosts) pertaining to the same base domain.
---

<div id="2"></div>

## 2. What is a domain?
> A domain name is the identity of one or more IP addresses.

Different Types of Domains;
1. Top-Level Domains (TLDs)
> Top-Level Domains (TLDs), sometimes called domain name extensions, are the part that comes right after your primary domain name.
(for example, the .com, net, io, etc).
2. Country Code Top-Level Domain (ccTLD)
> Country Code Top-Level Domains (ccTLDs) are restricted to use in specific countries
(for example, .ie, .uk, .us, .ca, etc).
3. Generic Top-Level Domain (gTLD)
> Generic top-level domains (gTLDs) are one of the categories of top-level domains (TLDs) maintained by the Internet Assigned Numbers Authority (IANA) for use in the Domain Name System of the Internet (for example, .com, .edu, .info, .org, .net, .gov, etc).
4. Second-Level Domain (SLD)
> A Second Level Domain (SLD) is the part of the domain name that is located right before a Top Level Domain (TLD).
5. Third-level domain
> A third-level domain name is the part of a domain name or website address that comes before the second-level domain name. Third-level domains are also called “sub-domains” as they sometimes refer to specific sections or pages of a website.
6. Premium Domain
> Premium domain names are high-quality domains that have been previously registered but are available for sale at today's market value.
---

<div id="3"></div>

## 3. What is DNS? A number of DNS records.
> DNS, or the Domain Name System, translates human readable domain names 

Common DNS Record Types:

| Record | Description |
| --- | --- |
| A | Address record (IPv4) |
| AAAA | Address record (IPv6) |
| CNAME | Canonical Name record |
| MX | Mail Exchanger record |
| NS | Nameserver record |
| PTR | Pointer record |
| SOA | Start of Authority record |
| SRV | Service Location record |
| TXT | Text record |
---
<div id="4"></div>

## 4. What is hosting, vps, server?

### 1. Hosing
> Web hosting is a service that allows organizations and individuals to post a website or web page onto the Internet.

> A web host, or web hosting service provider, is a business that provides the technologies and services needed for the website or webpage to be viewed in the Internet.

> Websites are hosted, or stored, on special computers called servers.

Example hosting provider: Bluehost, Hostgator, Hostinger, ..

### 2. VPS
> Virtual Private Server (VPS) is hosting that virtually mimics dedicated server environments within a shared server.

> VPS hosting has become a popular choice because it is generally lower in cost than dedicated hosting but provides better reliability, security, and performance than shared hosting.

Example VPS Hosting Provider: InMotion, A2 Hosting, Bluehost, iPage, HostGator, GreenGeeks, Hostinger, DreamHost, ....

### 3. Server
> In computing, a server is a piece of computer hardware or software that provides functionality for other programs or devices, called "clients". This architecture is called the client–server model.
---

<div id="5"></div>

## 5. What is reverse proxy, working principle?
> A reverse proxy server is a type of proxy server that typically sits behind the firewall in a private network and directs client requests to the appropriate backend server.

Common uses for a reverse proxy server:
1. Load Balancing.
> A reverse proxy server is sitting in front of your backend servers and distributing client requests across a group of servers in a manner that maximizes speed and capacity utilization while ensuring no one server is overloaded, which can degrade performance.
2. Web acceleration.
> Reverse proxies can compress inbound and outbound data, as well as cache commonly requested content, both of which speed up the flow of traffic between clients and servers. They can also perform additional tasks such as SSL encryption to take load off of your web servers.
3. Security and anonymity.
> A reverse proxy server protects their identities and acts as an additional defense against security attacks.

![reverse_proxy](./img/reverse_proxy.jpg)

> Reverse proxy accepts a request from a client, forwards it to a server that can fulfill it, and returns the server’s response to the client.
---

<div id="6"></div>

## 6. Comparison between Nginx and Apache?

| Comparison | Apache | Nginx |
| --- | --- | --- |
| Basic Architecture | <p> - Process Drive Approach </p> <p> - Creates a new thread for each request </p> | <p> - Event-Driven approach </p> <p> - Handles multiple requests within one thread </p> |
| Performance | <p> - Servers static content using the file-based metho </p> <p> - Processes dynamic content within the server </p> | <p> - Nginx serves static resources without using PHP </p> <p> - It doesn't process dynamic content </p> |
| OS Support | - Supports all Unix-like systems including Linux & BSD and fully supports MS-Windows. | - Supports almost all Unix-like OS and Windows partially. |
| Centralized Configuration | - Allows additional cofiguration on a per-directory basis via .htaccess files. | - Doesn't allow additional configuration. |
| Request Interpretation | - Passes file system location | - Passes URL to interpret requests. |
| Feature modules | - 60 official dynamically loadable modules that can be turned ON/OFF | - 3rd Party core modules (not dynamically loadable). |
| Flexibility | - Supports customization of web server through dynamic modules | - Not flexible enough to support dynaic modules and loading. |
| Sercuriy | - Great security | - Better security with the smaller codebase |
| Support | - Community support is done through mailing lists, IRC, and Stack Overflow | - Community support is done through mailing lists, IRC, and Stack Overflow and a forum |
