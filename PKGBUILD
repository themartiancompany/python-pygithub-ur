# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-pygithub
pkgname=('python-pygithub' 'python2-pygithub')
pkgver=1.35
pkgrel=1
pkgdesc="Use the full Github API v3"
arch=('any')
license=('LGPL')
url="https://github.com/PyGithub/PyGithub"
makedepends=('python-setuptools' 'python2-setuptools' 'python-pyjwt' 'python2-pyjwt')
source=("$pkgbase-$pkgver.tar.gz::https://github.com/PyGithub/PyGithub/archive/$pkgver.tar.gz")
sha512sums=('d852f459e5514310ac7bbb3cd9742a7269f9ea5c3e0fdfb0f385616fa31d35b72b19f63b650c60241c5e2f29860ddc35caa907a623c661bc77a29dfe4da3613b')

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
