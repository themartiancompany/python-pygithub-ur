# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-pygithub
pkgname=('python-pygithub' 'python2-pygithub')
pkgver=1.34
pkgrel=1
pkgdesc="Use the full Github API v3"
arch=('any')
license=('LGPL')
url="http://jacquev6.github.com/PyGithub"
makedepends=('python-setuptools' 'python2-setuptools' 'python-pyjwt' 'python2-pyjwt')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/PyGithub/PyGithub/archive/v$pkgver.tar.gz")
sha512sums=('59030fb737d57de6ba49f86fce085a13cb860b7c3ccf3cd76d5c5280ae398945bfc2351ed1e6e014a9fdd6e330ff6d67ed696c60d1f6e187f7c36589daba8aa5')

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
