# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_Pkg="PyGithub"
_pkg="pygithub"
pkgname="${_py}-${_Pkg}"
pkgver=2.5.0
pkgrel=2
pkgdesc="Use the full Github API v3"
arch=(
  'any'
)
license=(
  'LGPL'
)
_http="https://github.com"
_ns="${_Pkg}"
url="${_http}/${_ns}/${_Pkg}"
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
  "${_py}-deprecated"
  "${_py}-pyjwt"
  "${_py}-requests"
  "${_py}-pynacl"
  "${_py}-typing_extensions"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-setuptools-scm"
  "${_py}-wheel"
)
checkdepends=(
  'python-pytest'
  'python-cryptography'
  'python-httpretty'
  'python-parameterized'
)
_tarname="${_Pkg}-${pkgver}"
source=(
  "${_tarname}.tar.gz::${url}/archive/v${pkgver}.tar.gz"
)
sha512sums=(
  '4fbb6b27e21ba97ee59a0bafee40768d2beb61d9d405e2edd04bb859df7e299c072917dd7fde85202a539591d806e1a4697576cab78b465c559eef50fa223183'
)

build() {
  cd \
    "${_tarname}"
  SETUPTOOLS_SCM_PRETEND_VERSION=${pkgver} \
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${_tarname}"
  "${_py}" \
    -m pytest
}

package() {
  cd \
    "${_tarname}"
  "${_py}" \
    -m \
      installer \
      --destdir="${pkgdir}" \
      "dist/"*".whl"
}
