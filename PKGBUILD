# Maintainer: Christian Hesse <mail@eworm.de>

pkgname=vmware-view-open-client-beta
_realname=VMware-view-open-client
pkgver=4.5.0
_realver=4.5.0-297975
pkgrel=15
pkgdesc="VMware View Open Client connects to virtual machines managed by VMware View (beta version)"
conflicts=('vmware-view-client' 'vmware-view-open-client')
provides='vmware-view-open-client'
arch=('i686' 'x86_64')
url="http://code.google.com/p/vmware-view-open-client/"
license=('LGPL')
depends=('curl' 'boost' 'gtk2' 'openssl' 'libxml2' 'icu' 'intltool' 'rdesktop')
# this is the old URL, but it does no longer exist:
#http://vmware-view-open-client.googlecode.com/files/${_realname}-source-${_realver}.tar.gz
source=("http://www.eworm.de/download/linux/${_realname}-source-${_realver}.tar.gz"
	'curl-types.patch'
	'binutils-gold-x11.patch')

build() {
	cd "${srcdir}/${_realname}-source-${_realver}"

	patch -Np1 < ${srcdir}/curl-types.patch
	patch -Np1 < ${srcdir}/binutils-gold-x11.patch

	./configure --with-buildtype=release --prefix=/usr
	make
}

package() {
	cd "${srcdir}/${_realname}-source-${_realver}"

	make DESTDIR="${pkgdir}/" install
}

sha256sums=('8c81aed954419180c4b36807df15907b333c5558dd0b57650f3743af7c67702c'
            '14e7ef5731288a716fe31a7a012290a9a45ad0b9291507587c5b0f3a7e19191c'
            'bcd8570e95cad0b0a960ec52885f556ddfe7f0fd19e35d26e381be787feff34f')
