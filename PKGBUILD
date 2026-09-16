# Maintainer: Xilin Wu <sophon@radxa.com>

pkgname=libva-v4l2
pkgver=1.0.0
pkgrel=1
pkgdesc='VA-API backend for Qualcomm Iris V4L2 M2M video acceleration'
arch=('aarch64')
url='https://github.com/radxa-pkg/libva-v4l2'
license=('MIT')
depends=('gcc-libs' 'libva' 'libdrm' 'mesa' 'libglvnd')
makedepends=('git' 'meson' 'ninja' 'pkgconf')
source=("$pkgname::git+$url.git#tag=v$pkgver")
sha256sums=('SKIP')

prepare() {
  cd "$pkgname"
  git checkout "v$pkgver"
}

build() {
  meson setup build "$pkgname" \
    --prefix=/usr \
    --libdir=lib \
    --buildtype=plain \
    -Dfastcv=disabled
  meson compile -C build
}

package() {
  DESTDIR="$pkgdir" meson install -C build --no-rebuild
}
