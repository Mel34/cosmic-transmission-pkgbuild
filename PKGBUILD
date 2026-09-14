# Maintainer: Petar Margetić
pkgname=cosmic-transmission
pkgver=0.3.0
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
sha256sums=('44a78d2b8499b585af4fbf89a308f1f8d8220a2de08585604ad69ef8cfeb7179')

build() {
    cd "$pkgname-$pkgver"

    cargo build --release --locked
}

package() {
    cd "$pkgname-$pkgver"

    install -Dm755 \
        target/release/cosmic-transmission \
        "$pkgdir/usr/bin/cosmic-transmission"

    install -Dm644 \
        resources/cosmic-transmission.desktop \
        "$pkgdir/usr/share/applications/io.github.cosmic.Transmission.desktop"
}
