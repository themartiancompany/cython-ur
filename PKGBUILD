# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Igor Scabini <furester @ gmail.com>

pkgname=('cython' 'cython2')
pkgbase=cython
pkgver=0.24.1
pkgrel=1
pkgdesc="C-Extensions for Python "
arch=(i686 x86_64)
url="http://cython.org"
license=('APACHE')
makedepends=('python-setuptools' 'python2-setuptools')
source=("https://pypi.python.org/packages/c6/fe/97319581905de40f1be7015a0ea1bd336a756f6249914b148a17eefa75dc/Cython-$pkgver.tar.gz")
md5sums=('890b494a12951f1d6228c416a5789554')

package_cython() {
  depends=('python' 'python-setuptools')

  cd $srcdir/Cython-$pkgver
  python setup.py install --root=$pkgdir

  sed -i 's|#!.*python|#!/usr/bin/python3|' $pkgdir/usr/bin/*
}

package_cython2() {
  depends=('python2' 'python2-setuptools')

  cd $srcdir/Cython-$pkgver
  python2 setup.py install --root=$pkgdir

  mv $pkgdir/usr/bin/cygdb $pkgdir/usr/bin/cygdb2
  mv $pkgdir/usr/bin/cython $pkgdir/usr/bin/cython2
  mv $pkgdir/usr/bin/cythonize $pkgdir/usr/bin/cythonize2
}
