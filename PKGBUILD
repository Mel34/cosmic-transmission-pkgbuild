# Maintainer: Petar Margetić
pkgname=cosmic-transmission
pkgver=0.3.2
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
    "$pkgname-$pkgver.tar.gz::https://github.com/Mel34/cosmic-transmission/archive/refs/tags/$pkgver.tar.gz"
)

sha256sums=('f37b20bd56a983b255000ea4aee4e57c395ec6813c29cdfb54650317c09dc2a3')

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
