# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-pygithub
pkgname=('python-pygithub' 'python2-pygithub')
pkgver=1.33
pkgrel=1
pkgdesc="Use the full Github API v3"
arch=('any')
license=('LGPL')
url="http://jacquev6.github.com/PyGithub"
makedepends=('python-setuptools' 'python2-setuptools' 'python-pyjwt' 'python2-pyjwt')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/PyGithub/PyGithub/archive/v$pkgver.tar.gz")
sha512sums=('e33c8d16cb1ebbd874cb5e0ef4fb9c2a457331a820b44e73a23cddc385600eee341f0ba613cb29c0eab38e0406b26ccaabd637a8ef995e1dc9318241487eb353')

prepare() {
  cp -a PyGithub-$pkgver{,-py2}
}

build() {
  cd "$srcdir"/PyGithub-$pkgver
  python setup.py build

  cd "$srcdir"/PyGithub-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/PyGithub-$pkgver
  python setup.py test

  cd "$srcdir"/PyGithub-$pkgver-py2
  python2 setup.py test
}

package_python-pygithub() {
  depends=('python-pyjwt')

  cd PyGithub-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
}

package_python2-pygithub() {
  depends=('python2-pyjwt')

  cd PyGithub-$pkgver-py2
  python2 setup.py install --root="$pkgdir" --optimize=1
}
