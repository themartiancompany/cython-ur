# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=cython
pkgver=0.15
pkgrel=1
pkgdesc="C-Extensions for Python "
arch=(i686 x86_64)
url="http://www.cython.org"
license=('APACHE')
depends=('python2')
source=("http://cython.org/release/Cython-$pkgver.tar.gz")
md5sums=('794b93c4c1c4cc031f90302cacd834ca')

build() {
  cd $srcdir/Cython-$pkgver
  python2 setup.py install --root=$pkgdir
}
