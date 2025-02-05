# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer:  Antonio Rojas <arojas@archlinux.org>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>
# Contributor: Pellegrino Prevete <cGVsbGVncmlub3ByZXZldGVAZ21haWwuY29tCg== | base -d>
# Contributor: Truocolo <truocolo@aol.com>

_os="$( \
  uname \
    -o)"
if [[ "${_os}" == "Android" ]]; then
  _libc="ndk-sysroot"
  _pip="true"
  _build="false"
elif [[ "${_os}" == "GNU/Linux" ]]; then
  _libc="glibc"
  _pip="false"
  _build="true"
fi
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
pkgname=cython
pkgver=3.0.10
pkgrel=5
pkgdesc='C-Extensions for Python'
arch=(
  'x86_64'
  'arm'
  'i686'
  'armv7h'
  'pentium4'
  'aarch64'
  'powerpc'
)
url="https://${pkgname}.org"
license=(
  'APACHE'
)
depends=(
  "${_libc}"
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
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
  "${_py}-setuptools"
  "${_py}-wheel"
)
if [[ "${_pip}" == "true" ]]; then
  makedepends+=(
    "${_py}-pip"
  )
elif [[ "${_build}" == "true" ]]; then
  makedepends+=(
    "${_py}-build"
    "${_py}-installer"
  )
fi
checkdepends=(
  'gdb'
  "${_py}-numpy"
  "${_py}-pytest"
)
_http="https://github.com"
_url="${_http}/${pkgname}/${pkgname}"
source=(
  "${_url}/archive/$pkgver/$pkgname-$pkgver.tar.gz"
)
sha256sums=(
  "00f97476cef9fcd9a89f9d2a49be3b518e1a74b91f377fe08c97fcb44bc0f7d7"
)

build() {
  cd \
    "${pkgname}-${pkgver}"
  if [[ "${_build}" == "true" ]]; then
    "${_py}" \
      -m build \
        --wheel \
        --no-isolation
  fi
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
  if [[ "${_build}" == "true" ]]; then
    "${_py}" \
      -m installer \
      --destdir="${pkgdir}" \
      "dist/"*".whl"
  elif [[ "${_pip}" == "false" ]]; then
    pip \
      install \
        "${pkgname}" \
        -t \
          "${pkgdir}"
  fi
  for f \
    in cygdb cython cythonize; do
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
