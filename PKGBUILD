# Maintainer: Sung Pae <self@sungpae.com>
pkgname=fakedeps
pkgver=29
pkgrel=1
pkgdesc="A dummy package that satisfies unwanted dependencies."
arch=('any')
license=('GPL')
groups=('nerv')
provides=(
    at-spi2-atk
    at-spi2-core
    avahi
    colord{,-gtk}
    geoclue2
    gnome-online-accounts
    gst-plugins-bad
    gvfs
    libcloudproviders
    libcolord
    polkit
    rtkit
    xdg-desktop-portal
)
conflicts=("${provides[@]}")
replaces=("${provides[@]}")

_package_lib() {
    gcc "lib/$1" -shared -o "lib/$2"
    install -Dm 0755 "lib/$2" "$pkgdir/usr/lib/$2"
    local link
    for link in "${@:3}"; do
        ln -s "$2" "$pkgdir/usr/lib/$link"
    done
}

package() {
    cd "$startdir"

    _package_lib libatk-bridge-2.0.c libatk-bridge-2.0.so{,.0,.0.0.0}
    _package_lib libatspi.c          libatspi.so{,.0}
    _package_lib libavahi-client.c   libavahi-client.so{,.3,.3.2.9}
    _package_lib libavahi-common.c   libavahi-common.so{,.3,.3.5.3}
    _package_lib libavahi-ui-gtk3.c  libavahi-ui-gtk3.so{,.0}
    _package_lib libcloudproviders.c libcloudproviders.so{,.0,.0.2.5}
    _package_lib libcolord-gtk.c     libcolord-gtk.so{,.1,.1.0.3}
    _package_lib libcolord.c         libcolord.so{,.2,.2.0.5}

    install -d "$pkgdir/usr/lib/pkgconfig"
    install -m 0644 lib/pkgconfig/*.pc "$pkgdir/usr/lib/pkgconfig/"
}
