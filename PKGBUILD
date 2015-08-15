# Maintainer: Limao Luo <luolimao+AUR@gmail.com>

pkgname=granola-gui
pkgver=5.0.6
pkgrel=3
pkgdesc="MiserWare Granola graphical interface"
arch=(i686 x86_64)
url=http://personal.grano.la/
license=(custom)
depends=(python2-dbus gksu 'granola>=5' gtk2 pygtk python2-gconf)
options=(!strip)
install=$pkgname.install
if [[ $CARCH = "i686" ]]; then
    _arch=i386
    sha256sums=('85a3bbaf5c05b3b0852d0a007efeec9a43f9b5fd09faa84ef614c4681d99c857')
    sha512sums=('0e6b2097b1848d348f7a70c6eee6a1cc2c016c26131fb2680c36c1905826d16d337034a2e7df3849211686223d6891974667cbd9886a129d1954082d20552d88')
else
    _arch=$CARCH
    sha256sums=('40e0ab3b88d4cc557e88b0c07058f7cdb4687a23305b88ad53c8e9c89c4ba9b1')
    sha512sums=('7461fe61292ded2bf7f99e35935bb57ca3d45d613b7b127c38f504a6b87bb590ba014989830d1baee9857641f8c537daabf83ff46dca94d1e6112a829bf92925')
fi
source=(https://download.miserware.com/linux/tar/$_arch/$pkgname-$pkgver-$_arch.tar.gz)

build() {
    sed -i 's:^#!/usr/bin/python$:&2:' "$srcdir"/$pkgname-$pkgver-$_arch/usr/bin/$pkgname
}

package() {
    cd "$srcdir"/$pkgname-$pkgver-$_arch/
    cp -r usr "$pkgdir"
    [[ $CARCH = "x86_64" ]] && mv "$pkgdir"/usr/lib64/ "$pkgdir"/usr/lib/

    rm -rf "$pkgdir"/usr/share/doc/
    install -Dm644 usr/share/doc/$pkgname-$pkgver/LICENSE.txt "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
