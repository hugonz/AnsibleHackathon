# The Certocalypse
## Ansible's big technical opportunity for 2026-2030


### What's happening with public key certificates?
We used to buy or provision public key certificates valid for years or hundreds of days (60 months, 39 months, or 825 days, in the past), install them manually and set reminders to do it all over again in a year or more. The satate-of-the-art automation tool for certificates was a calendar reminder.

Since 2026 and all the way into 2029, all certificate providers will start **reducing the duration** of new certificates. This is the timeline:

| date | max certificate life |deadline
|----------|----------------------|-------|
|< March 15, 2026 | 398 days ||
|< March 15, 2027 | 200 days | The Certagility |
|< March 15, 2029 | 100 days | Y2Cert approaching |
|**>= March 15, 2029** | **47 days** | The Certocalypse |

Increasingly it will be **from hard to impossible** to manually detect upcoming certificate expiration, manually renew or purchase them and manually install the certificates into the applications, servers, appliances, etc.

 ![Certocalypse timeline](/assets/images/timeline.png)
 
### What about my own certificates, self-signed or from a private Certificate Autority(CA)?
There's a historical trend from browser and cloud vendors to stop accepting any certificates with longer validity, no matter if they're public or private. It will be necessary to limit our own certificates so that they fall within the max duration in the previous table (47 days starting in 2029)

So, you should plan for moving *all certificates*, self-signed, and private CA issued, to <47 days by 2029.

### What can Ansible Automation Platform do?

AAP can automate the full lifecycle:

#### 1. Detection or inventory of certificate expiration, weakness or problems

#### 2. Generation of certificates from a public certificate provider, from an internal Certificate Authority or tool, or generation of self-signed certificates. Some tools are:

  - RHEL itself and OpenSSL
  - Red Hat Certificate System
  - Microsoft Windows Domain Controllers (with Certificate Authority Role)
  - Cyberark Certificate Manager
  - Hashicorp Vault
  - AWS Certificate Manager
  - DigiCert
  - Actalis
  - Verisign

####  3. Installation and maintenance of certificates in
   -  Linux, Windows servers and other platforms
   -  Application servers, Java ecosystems and databases
   -  Networks appliances, proxies, load balancers and API managers
   -  Public and private cloud services
   -  Openshift and Kubernetes services


