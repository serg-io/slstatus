# Originally copied from [AUR](https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=slstatus-git).

# Maintainer: Ankit R Gadiya <arch@argp.in>

pkgname=slstatus
pkgver=0.0.1
pkgrel=1
pkgdesc="A status monitor for window managers"
arch=('i686' 'x86_64')
url="http://tools.suckless.org/slstatus"
depends=('libx11')
makedepends=('git')
license=('custom:ISC')

prepare() {
  # Create a directory in srcdir and cd into it.
  mkdir -p $srcdir/$pkgname-$pkgver
  cd "$srcdir/$pkgname-$pkgver"

  # Copy all files at the root of the repo into the new directory and ignore errors.
  cp $startdir/* . 2> /dev/null || true
  cp -r $startdir/components .

  # Remove unneeded files.
  rm -f PKGBUILD README.md $pkgname-*.tar.xz
}

build() {
  cd "$srcdir/$pkgname-$pkgver"
  make X11INC="/usr/include/X11" X11LIB="/usr/lib/X11"
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make PREFIX="/usr" DESTDIR="$pkgdir" install

  install -m644 -D LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -m644 -D README "$pkgdir/usr/share/doc/$pkgname/README"
}
