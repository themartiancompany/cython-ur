# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=cython
pkgver=0.14
pkgrel=1
pkgdesc="C-Extensions for Python "
arch=(i686 x86_64)
url="http://www.cython.org"
license=('APACHE')
depends=('python2')
source=("http://cython.org/release/Cython-$pkgver.tar.gz")
md5sums=('27fa072e8282431864543e008fd9a19b')

build() {
  cd $srcdir/Cython-$pkgver
  python2 setup.py install --root=$pkgdir
}
