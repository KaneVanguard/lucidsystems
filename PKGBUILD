# Maintainer: Kane Vanguard

pkgname=lucidsystems
pkgver=20140912
pkgrel=1
pkgdesc="LucidSystems meta package"
arch=('any')
depends=('lucidsystems-desktop-environment' 'lucidsystems-artwork' 'luicdsystems-config')
makedepends=('bash' 'wget')
provides=('lsb-release')
conflicts=('lsb-release')
url="https://github.com/KanVanguard/lucidsystems"
license=('GPL')
groups=('lucidsystems')

LSB_VERSION=1.0

build() {
    cd "$srcdir"
    wget http://downloads.sourceforge.net/lsb/lsb-release-$LSB_VERSION.tar.gz
    tar xvfz lsb-release-$LSB_VERSION.tar.gz
    
    cd lsb-release-$LSB_VERSION
    make
}

package() {
    cd "$srcdir"

    install -dm755 "$pkgdir/etc"
    echo "LSB_VERSION=$LSB_VERSION" >> "$pkgdir/etc/lsb-release"
    echo "DISTRIB_ID=bbqlinux" >> "$pkgdir/etc/lsb-release"
    echo "DISTRIB_RELEASE=rolling" >> "$pkgdir/etc/lsb-release"
    echo "DISTRIB_DESCRIPTION=\"BBQLinux\"" >> "$pkgdir/etc/lsb-release"
    echo "DISTRIB_CODENAME=" >> "$pkgdir/etc/lsb-release"
    
    install -Dm 644 lsb-release-$LSB_VERSION/lsb_release.1.gz "$pkgdir/usr/share/man/man1/lsb_release.1.gz"
    install -Dm 755 lsb-release-$LSB_VERSION/lsb_release "$pkgdir/usr/bin/lsb_release"
}
