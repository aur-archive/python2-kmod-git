# Maintainer: Your Name <youremail@domain.com>

build() {
  # lolyaourt
  :
}

pkgname=python2-kmod-git
pkgver=20120503
pkgrel=1
pkgdesc="python bindings for libkmod"
arch=('i686' 'x86_64')
url="https://github.com/agrover/python-kmod"
license=('GPL2')
depends=('python')
makedepends=('python2-distribute')
provides=('python2-kmod')
conflicts=('python2-kmod')

_gitroot="git://github.com/agrover/python-kmod.git"
_gitname="python-kmod"

build() {
  msg "Connecting to GIT server...."

  if [[ -d $_gitname ]] ; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  cp -r "$srcdir/$_gitname" "$srcdir/$_gitname-build"

  cd "$srcdir/$_gitname-build"
  python2 setup.py build
}

package() {
  cd "$srcdir/$_gitname-build"
  python2 setup.py install --root="$pkgdir/" --optimize=1
}

# vim:set ts=2 sw=2 et:
