# Maintainer: Petar Margetić
pkgname=cosmic-transmission
pkgver=0.4.0
pkgrel=1
pkgdesc='COSMIC applet for controlling the Transmission daemon'
arch=('x86_64')
url='https://github.com/Mel34/cosmic-transmission'
license=('GPL-3.0-only')

depends=(
    'cosmic-applets'
    'systemd'
    'xdg-utils'
)

makedepends=(
    'cargo'
)

source=(
    "$pkgname-$pkgver.tar.gz::https://github.com/Mel34/cosmic-transmission/archive/refs/tags/v$pkgver.tar.gz"
)

sha256sums=('062335d531049a4ce491e1b35500d0d7a5545c7c0a745e7c1d785220d73cab49')

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

    install -Dm644 \
        resources/cosmic-transmission.desktop \
        "$pkgdir/usr/share/applications/io.github.cosmic.Transmission.desktop"
}
