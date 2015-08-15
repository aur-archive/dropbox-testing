# Modify from:

# Maintainer: Massimiliano Torromeo <massimiliano.torromeo@gmail.com>
# Contributor: Tom < tomgparchaur at gmail dot com >

pkgname=dropbox-testing
pkgver=1.3.14
pkgrel=1
pkgdesc="the testing version of dropbox"
arch=("i686" "x86_64")
url="http://www.dropbox.com"
license=(custom)
depends=("bzip2" "dbus-glib" "gtk2" "libsm")
conflicts=("dropbox-experimental")
options=('!strip')

_source_arch="x86"
[ "$CARCH" = "x86_64" ] && _source_arch="x86_64"

md5sums=('3ee4defeeface3049cecce646dc9f1ff' '9ec50da2ce59ed8c17606394b9c5e1c0' 'a9dbde2f71bde14730a5ff9e3bd13ff8' '5331288d5f5972dc2e9311d0f28dac76')
[ "$CARCH" = "x86_64" ] && md5sums[0]='51911323f7dbca076c7403971df634c9'

source=("https://dl-web.dropbox.com/u/17/dropbox-lnx.${_source_arch}-${pkgver}.tar.gz" "dropbox.png" "dropbox.desktop" "terms.txt")

build() {
	install -d "$pkgdir/opt"
	rm "$srcdir/.dropbox-dist/libstdc++.so.6"
	cp -R "$srcdir/.dropbox-dist" "$pkgdir/opt/dropbox"

	find "$pkgdir/opt/dropbox/" -type f -exec chmod 644 {} \;
	find "$pkgdir/opt/dropbox/" -type d -exec chmod 755 {} \;
	chmod 755 "$pkgdir/opt/dropbox/dropboxd"
	chmod 755 "$pkgdir/opt/dropbox/dropbox"
	chown -R root:root "$pkgdir/opt/dropbox"

	install -d "$pkgdir/usr/bin"
	ln -s "/opt/dropbox/dropboxd" "$pkgdir/usr/bin/dropboxd"

    install -D -m 644 "$srcdir/dropbox.desktop" "$pkgdir/usr/share/applications/dropbox.desktop"
	install -D -m 644 "$srcdir/dropbox.png" "$pkgdir/usr/share/pixmaps/dropbox.png"
	install -D -m 644 "$srcdir/terms.txt" "$pkgdir/usr/share/licenses/$pkgname/terms.txt"
}
