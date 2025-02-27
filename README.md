# certctl
Modified version of FreeBSD's certctl(8)

Adds the ability to generate CAfile bundles in addition to CApath.

OpenSSL provides two ways of accessing a PKI store: CApath and CAfile.
The CAfile format was historically supported by the security/ca_root_nss
port.  However, two separately installed and managed trust store sources
is untenable.  This project solves that by extending certctl(8) to provide
both formats to support software that can't or won't use a CApath.
