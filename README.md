# certctl
Modified version of FreeBSD's certctl(8)

Adds the ability to generate a CAfile certificate bundle along side the
CApath in /etc/ssl/certs.  Provides the same certificate bundle
security/ca_root_nss installs, but maintains important features like
support for local certificates.

If ports can force cert.pem to be present, and OpenSSL won't use both in
tandem, I need something a little better than two separate sources with
feature disparity.
