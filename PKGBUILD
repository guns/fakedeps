# Maintainer: Sung Pae <self@sungpae.com>
pkgname=fakedeps
pkgver=2
pkgrel=1
pkgdesc="A dummy package that satisfies unwanted dependencies."
arch=('any')
license=('GPL')
groups=('nerv')
provides=(polkit rtkit avahi at-spi2-atk gvfs)
conflicts=(polkit rtkit avahi at-spi2-atk gvfs)
replaces=(polkit rtkit avahi at-spi2-atk gvfs)

package() {
    cd "$startdir"

    gcc libatk-bridge-2.0.c -shared -o libatk-bridge-2.0.so
    install -Dm 0755 libatk-bridge-2.0.so "$pkgdir/usr/lib/libatk-bridge-2.0.so"
    ln -s libatk-bridge-2.0.so "$pkgdir/usr/lib/libatk-bridge-2.0.so.0"
    ln -s libatk-bridge-2.0.so "$pkgdir/usr/lib/libatk-bridge-2.0.so.0.0.0"
}
