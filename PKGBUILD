# Maintainer: Antony Ho <ntonyworkshop@gmail.com>
pkgname=ibus-cangjie-git
pkgver=d920c06
pkgrel=1
pkgdesc="This is an IBus engine for users of the Cangjie and Quick input methods."
arch=(any)
url="https://github.com/bochecha/ibus-cangjie"
license=('(L)GPL3')
depends=('ibus>=1.4.1' 'pycangjie-git' 'python>=3.2' 'python-gobject')
makedepends=('git' 'autoconf')
replaces=('ibus-cangjie')
sha1sums=('SKIP')
_gitroot="git://github.com/bochecha/ibus-cangjie.git"
_gitname="ibus-cangjie"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server..."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $gitname
  fi
  msg "GIT checkout done or server timeout"

  cd "$srcdir/$_gitname"
  ./autogen.sh
  ./configure --prefix=/usr
  make
}

pkgver() {
  cd "$srcdir/$_gitname"
  echo $(git rev-parse --short HEAD)
}

package() {
  cd "$srcdir/$_gitname"
  make DESTDIR="$pkgdir/" install
}
