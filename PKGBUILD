pkgname=koompi-libinput
pkgver=1.17.0
pkgrel=1
pkgdesc="Input device management and event handling library"
url="https://www.freedesktop.org/wiki/Software/libinput/"
arch=(x86_64)
license=(custom:X11)
depends=('mtdev' 'libevdev' 'libwacom')
provides=('libinput')
conflicts=('libinput')
# upstream doesn't recommend building docs
makedepends=('gtk3' 'meson') # 'doxygen' 'python-sphinx' 'python-recommonmark'
optdepends=('gtk3: libinput debug-gui'
            'python-pyudev: libinput measure'
            'python-evdev: libinput measure'
            'xorg-xinput: input configuration for X')
source=(
  "libinput-$pkgver.tar.gz"
)
sha256sums=(
  "18630f7d037f6140c397d2a5b4aa2d0ad25b785866e2033608c9c174aae5f910"
)

preprare(){
  cd "${srcdir}"
  tar -zxf libinput-1.17.0.tar.gz
}

build() {
  cd "${srcdir}"/libinput-1.17.0
  meson --prefix=/usr  "${srcdir}"/libinput-1.17.0/builddir/
  ninja $NINJAFLAGS -C "${srcdir}"/libinput-1.17.0/builddir/
}

package() {
  DESTDIR="$pkgdir" ninja -C "${srcdir}"/libinput-1.17.0/builddir/ install

  install -Dvm644 "${srcdir}"/libinput-1.17.0/COPYING \
    "$pkgdir/usr/share/licenses/libinput/LICENSE"
}
