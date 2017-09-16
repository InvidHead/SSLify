![logo](https://raw.githubusercontent.com/InvidHead/SSLify/master/logo.png)
## WTF is it
It can rapidly provide your server SSL support with out purchasing, waiting...

Where you can use:

| Name        | Description           | 
| ------------- |-------------| 
| iOS APP Development | iOS Development restricted developers to use SSL when communicating with server| 
| Beautify Address | Who don't like the address started with green locks |
| And more... | |

But remember!! Do **NOT** use this in production. Never!

Users may kill you!!

## Why Us
A simple comparison

|| XIP.io | SSLip.io | Our SSLify |
----|----|------|----
Price | Free  | Private | Free
Unlimited Domains | ✓  | ✓ | ✓
Fast Wildcard DNS | ✓  | ✓ | ✓
SSL | ✗  | ✓ | ✓
Local Deployment | Hard  | Hard | Easy
Auto SSL Deploy  | ✗  | ✗ | ✓
Multi-lingual | ✗  | ✗ | ✓
Stable DNS | ✗  | ✗ | ✓
No Privacy Leaks | ✓  | ✗ | ✓
Concept | Local DNS Server  | Local DNS Server | CloudFlare

## How does it work

When user already deployed our public key and private key onto their server, they can now bind their server to our domain just like DNS control pannel.

Supported Record Types:

| Type        | Description           | 
| ------------- |-------------| 
| CNAME         | Used to specify that a domain name is an alias for another domain | 
| A             | Used to specify that an IP is an alias for a domain | 

The backend, after recveiving the GET request of creating domain, communicate with CloudFlare API and edit the DNS setting for our domain zone.

```Python
def dns(type,name,content):
    if type == "A":
        return [{'name':name, 'type':'A', 'content':content}]
    elif type == "CNAME":
        return [{'name':name, 'type':'CNAME', 'content':content}]

def push(dns_records):
    for dns_record in dns_records:
        r = cf.zones.dns_records.post(zone_id, data=dns_record) 
```

## Installation

```
git clone https://github.com/InvidHead/SSLify.git && cd SSLify
pip install -r requirements.txt
python server.py
```

For errors, please submit issues.
## Contributors

Shou Chaofan (scf@ieee.org)
