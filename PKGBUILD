# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=('cython' 'cython2')
pkgbase=cython
pkgver=0.16
pkgrel=1
pkgdesc="C-Extensions for Python "
arch=(i686 x86_64)
url="http://www.cython.org"
license=('APACHE')
makedepends=('python-distribute' 'python2-distribute')
source=("http://cython.org/release/Cython-$pkgver.tar.gz")
md5sums=('7934186ada3552110aba92062fa88b1c')

build() {
  true
}

package_cython() {
  depends=('python')

  cd $srcdir/Cython-$pkgver
  python setup.py install --root=$pkgdir
}

package_cython2() {
  depends=('python2')

  cd $srcdir/Cython-$pkgver
  python2 setup.py install --root=$pkgdir

  mv $pkgdir/usr/bin/cygdb $pkgdir/usr/bin/cygdb2
  mv $pkgdir/usr/bin/cython $pkgdir/usr/bin/cython2
}
