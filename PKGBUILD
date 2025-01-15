# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>

pkgbase='mkimg-th1520'
pkgname='lpi4a-bt'
pkgdesc='Bluetooth service for Lichee Pi 4A'
pkgver=20240720
pkgrel=1
url='https://github.com/revyos/mkimg-th1520'
arch=(riscv64)
license=('proprietary')
source=("https://github.com/revyos/${pkgbase}/archive/refs/tags/${pkgver}.tar.gz")
sha256sums=('f2983044d141a45f12b842e18d92c7211352479a8e65674de7a61e442f9b02c3')

build() {
  cd "$srcdir/$pkgbase-$pkgver/addons/$pkgname/package/rtk-hciattach/src"
  make -j $(nproc) CC="gcc -O2 $CFLAGS"
}

package() {
  cd "$srcdir/$pkgbase-$pkgver/addons"
  install -Dm644 etc/systemd/system/auto-hciattach.service \
    "${pkgdir}/etc/systemd/system/auto-hciattach.service"
  install -Dm755 lpi4a-bt/package/rtk-hciattach/src/rtk_hciattach \
    "${pkgdir}/usr/local/bin/rtk_hciattach"
}

# vim:set ts=8 sts=2 sw=2 et:
