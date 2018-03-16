# Easily configure your OpenLDAP server

## Disclaimer and dependencies

The tools has been developed and tested on Debian 9 only. Some packages are
needed:

```
% apt install debconf ldap-utils slapd
```

The TLS certificates have been generated by [`certbot`][certbot]
([Let's Encrypt][letsencrypt]).

## Usage

First you need to generate a `dhparam.pem` file by using this command:

```
% openssl dhparam -out /etc/letsencrypt/live/dhparam.pem 4096
```

The `numbits` parameter can be replaced by 2048 it the generation take too long.

Then clone the repository and run the `slapd-configure` script. It will ask you
some questions in order to properly configure your OpenLDAP server:

```
% git clone https://github.com/jmlemetayer/slapd-configure.git
% ./slapd-configure/slapd-configure
Remove old database? [Y/n] y
Enter Admin Password: ********
Retype Admin Password: ********
Enter Config Password: ********
Retype Config Password: ********
TLS private key file (privkey.pem): /etc/letsencrypt/live/ldap.jml.bzh/privkey.pem
TLS server certificate file (cert.pem): /etc/letsencrypt/live/ldap.jml.bzh/cert.pem
TLS CA certificate file (fullchain.pem): /etc/letsencrypt/live/ldap.jml.bzh/fullchain.pem
TLS DH parameter file (dhparam.pem): /etc/letsencrypt/live/dhparam.pem
```

## License

The `slapd-configure` script has been inspired by the
[@osixia/docker-openldap] project.

The `slapd-configure` script is released under the [MIT License][mit].

[certbot]: https://certbot.eff.org
[letsencrypt]: https://letsencrypt.org
[@osixia/docker-openldap]: https://github.com/osixia/docker-openldap
[mit]: https://opensource.org/licenses/MIT