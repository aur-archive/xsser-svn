# Maintainer: marc0s <marc0s@fsfe.org>
pkgname=xsser-svn
pkgver=25
pkgrel=1
pkgdesc="A penetration testing tool for detecting and exploiting XSS vulnerabilites."
provides=xsser
arch=('any')
url="http://xsser.sourceforge.net/"
license=('GPL3')
groups=('network')
depends=('orbited' 'python2' 'python-beautifulsoup' 'python-pycurl' 'twisted'
         'pygtk')
makedepends=('subversion')
optdepends=('pygtkmoz')

_svntrunk="https://xsser.svn.sourceforge.net/svnroot/xsser/"
_svnmod="xsser"

install=
changelog=
source=()
noextract=()
md5sums=() #generate with 'makepkg -g'

build() {
  cd "${srcdir}"
  msg "Starting SVN checkout..."
  if [ -d $_svnmod/.svn ] ; then
    cd $_svnmod && svn up
  else
    svn export $_svntrunk --config-dir ./ $_svnmod
  fi

  msg "SVN export done or server timeout"

  msg "Copying files..."
  cd $srcdir/$_svnmod
  python2 setup.py install --prefix=/usr --root="$pkgdir" || return 1
}


# vim:set ts=2 sw=2 et:
