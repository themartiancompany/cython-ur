# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer:  Antonio Rojas <arojas@archlinux.org>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>
# Contributor: Pellegrino Prevete <cGVsbGVncmlub3ByZXZldGVAZ21haWwuY29tCg== | base -d>
# Contributor: Truocolo <truocolo@aol.com>

_py="python"
pkgname=cython
pkgver=3.0.7
pkgrel=1
pkgdesc='C-Extensions for Python'
arch=(
  x86_64
  arm
  i686
  armv7h
  pentium4
  aarch64
  powerpc
)
url="https://${pkgname}.org"
license=(APACHE)
depends=(
  glibc
  "${_py}"
)
replaces=(
  "${pkgname}-dev"
)
provides=(
  "${_py}-${pkgname}=${pkgver}"
)
conflicts=(
  "${_py}-${pkgname}"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-setuptools"
  "${_py}-wheel"
)
checkdepends=(
  gdb
  "${_py}-numpy"
  "${_py}-pytest"
)
_url="https://github.com/${pkgname}/${pkgname}"
source=(
  "${_url}/archive/$pkgver/$pkgname-$pkgver.tar.gz"
)
sha256sums=(
  '50e72ac8e32f5cca8242ad319df4cbd1f76545f2b66bc5d7b17ce45d5cbc415e'
)

build() {
  cd \
    "${pkgname}-${pkgver}"
  "${_py}" \
    -m build \
      --wheel \
      --no-isolation
}

check() {
  cd \
    "${pkgname}-${pkgver}"
  "${_py}" \
    -m venv \
      --system-site-packages \
      test-env
  "test-env/bin/${_py}" \
    -m installer \
      dist/*.whl
  "test-env/bin/${_py}" \
    -m pytest \
      -v \
      --ignore docs \
      --ignore pyximport/test/test_reload.py \
      --ignore Cython/Debugger/Tests
}

package() {
  cd \
    "${pkgname}-${pkgver}"
  "${_py}" \
    -m installer \
    --destdir="${pkgdir}" \
    dist/*.whl

  for f in cygdb cython cythonize; do
    mv \
      "${pkgdir}/usr/bin/${f}" \
      "${pkgdir}/usr/bin/${f}3"
    ln \
      -s \
      ${f}3 \
      "$pkgdir/usr/bin/${f}"
  done
}

# vim:set sw=2 sts=-1 et:
