# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=cython
pkgver=0.14.1
pkgrel=1
pkgdesc="C-Extensions for Python "
arch=(i686 x86_64)
url="http://www.cython.org"
license=('APACHE')
depends=('python2')
source=("http://cython.org/release/Cython-$pkgver.tar.gz")
md5sums=('6341bf3b2c49a39b8046219f6696f5c4')

build() {
  cd $srcdir/Cython-$pkgver
  python2 setup.py install --root=$pkgdir
}
