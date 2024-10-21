## How to secure an NGINX server with Fail2Ban

Ban bots and scanners from sniffing in your NGINX server

## Instalation

Refer to [official Fail2Ban documentation](https://github.com/fail2ban/fail2ban/wiki/How-to-install-fail2ban-packages) for installing Fail2Ban in your server

## Configuration

There's 2 parts of the configuration;

1. Fail2Ban jail config file
2. Filter config file

E.g for installing _NoWordpress_ filter you must copy the filter file inside /etc/fail2ban/filter.d/ folder and copy the configuration part in jail config file located in /etc/fail2ban/jail.local

## Filters

- NoWordpress: Ban IPs trying to access known/default wordpress endpoints
- NoScript: Ban IPs trying to execute scripts
- NoProxy: Ban IPs trying to use server as proxy
- NoAgent: Ban IPs with no agent
- NoAuth: Ban IPs that fail to authenticate using NGINX HTTP basic authentication

You can add more filters for other needs like 401 or 403 responses following the same logic

<br>

> [!IMPORTANT]
> Run `sudo systemctl restart fail2ban` for config to take effect.

## Testing

You can test your filters with command:

```
fail2ban-regex <log file=""> <filter configuration="">
```

E.g.

```
fail2ban-regex /var/log/nginx/access.log /etc/fail2ban/filter.d/nginx-nowordpress.conf
```
