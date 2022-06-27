# Maintainer: Cleararch Group <jackeyz2022@mail.ru>
# Contributor: Chocobo1 <chocobo1 AT archlinux DOT net>

pkgname=dpkg
pkgver=1.21.1ubuntu2.1
pkgrel=1
pkgdesc="Ubuntu(A Branch of Debian) package management system"
arch=('i686' 'x86_64')
url="https://packages.ubuntu.com/jammy-updates/dpkg"
license=('GPL')
depends=('glibc' 'bzip2' 'perl' 'xz' 'zlib' 'zstd')
makedepends=('git' 'perl-io-string' 'perl-timedate')
source=("http://mirrors.163.com/ubuntu/pool/main/d/dpkg/dpkg_1.21.1ubuntu2.1.tar.xz")
sha256sums=('SKIP')

build() {
  cd "dpkg-"$pkgver

  ./autogen
  ./configure \
    --prefix="/usr" \
    --sbindir="/usr/bin" \
    --sysconfdir="/etc" \
    --localstatedir="/var" \
    --disable-start-stop-daemon
  make
}

package() {
  cd "dpkg-"$pkgver

  make DESTDIR="$pkgdir" install

  install -d "$pkgdir/var/dpkg/updates"
  touch "$pkgdir/var/lib/dpkg"/{status,available}
}
