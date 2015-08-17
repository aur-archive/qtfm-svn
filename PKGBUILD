# Maintainer: Michal Rost <rost.michal@gmail.com>
pkgname=qtfm-svn
pkgver=20130525
pkgrel=1
pkgdesc="A lightweight, multi-platform, and open source file manager. This package contains the latest version of QtFM, please use it instead of qtfm package in community."
url="http://code.google.com/p/qtfm/"
license=('GPL')
arch=('i686' 'x86_64')
source=()
depends=('qt4>=4.8')
makedepends=('subversion')
md5sums=()
provides=('qtfm')
conflicts=('qtfm')

# SVN location
_svntrunk=http://qtfm.googlecode.com/svn/trunk

# Build qtfm
build() {
  svn co $_svntrunk
  msg "SVN checkout done or server timeout"
  msg "Starting make..."

  BUILDDIR=${srcdir}/build
  mkdir -p $BUILDDIR
  cd $BUILDDIR

  qmake-qt4 -makefile ${srcdir}/trunk/qtfm.pro

  PROCS=`cat /proc/cpuinfo | grep processor | wc -l`
  make -j
}

# Create package
package() {
  mkdir -p ${pkgdir}/usr/bin
  mkdir -p ${pkgdir}/usr/share/pixmaps
  mkdir -p ${pkgdir}/usr/share/applications
  cp ${srcdir}/build/qtfm ${pkgdir}/usr/bin
  cp ${srcdir}/trunk/images/qtfm.png ${pkgdir}/usr/share/pixmaps
  cp ${srcdir}/trunk/qtfm.desktop ${pkgdir}/usr/share/applications
}
