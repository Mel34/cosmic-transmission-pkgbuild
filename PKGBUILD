# Maintainer: Petar Margetić
pkgname=cosmic-transmission
pkgver=0.5.0
pkgrel=1
pkgdesc='COSMIC applet for controlling the Transmission daemon'
arch=('x86_64')
url='https://github.com/Mel34/cosmic-transmission'
license=('GPL-3.0-only')

depends=(
    'cosmic-applets'
    'polkit'
    'systemd'
    'xdg-utils'
)

makedepends=(
    'cargo'
)

source=(
    "$pkgname-$pkgver.tar.gz::https://github.com/Mel34/cosmic-transmission/archive/refs/tags/v$pkgver.tar.gz"
)

sha256sums=('95a7a650f79a68bda477d332214919e07e1579cf1cf539ea8211b3ffec98c9ee')

build() {
    cd "$srcdir/cosmic-transmission-$pkgver"

    cargo build --release --locked
}

package() {
    cd "$srcdir/cosmic-transmission-$pkgver"

    install -Dm755 \
        target/release/cosmic-transmission \
        "$pkgdir/usr/bin/cosmic-transmission"

    install -Dm755 \
        target/release/cosmic-transmission-settings \
        "$pkgdir/usr/bin/cosmic-transmission-settings"

    install -Dm755 \
        target/release/cosmic-transmission-helper \
        "$pkgdir/usr/bin/cosmic-transmission-helper"

    install -Dm644 \
        resources/cosmic-transmission.desktop \
        "$pkgdir/usr/share/applications/io.github.cosmic.Transmission.desktop"

    install -d "$pkgdir/usr/share/icons"

    cp -a \
        data/icons/hicolor \
        "$pkgdir/usr/share/icons/"

    install -Dm644 \
        resources/io.github.cosmic.Transmission.Helper.service \
        "$pkgdir/usr/share/dbus-1/system-services/io.github.cosmic.Transmission.Helper.service"

    install -Dm644 \
        resources/io.github.cosmic.Transmission.Helper.conf \
        "$pkgdir/usr/share/dbus-1/system.d/io.github.cosmic.Transmission.Helper.conf"

    install -Dm644 \
        resources/io.github.cosmic.Transmission.policy \
        "$pkgdir/usr/share/polkit-1/actions/io.github.cosmic.Transmission.policy"

    install -Dm644 \
        resources/cosmic-transmission-helper.service \
        "$pkgdir/usr/lib/systemd/system/cosmic-transmission-helper.service"
}
