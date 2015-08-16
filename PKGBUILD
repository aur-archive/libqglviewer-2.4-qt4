# Maintainer: Baptiste Jonglez <baptiste--aur at jonglez dot org>
# Contributor: Gianluca Montecchi <gian@grys.it>
# Contributor: Geoffroy Carrier <geoffroy.carrier@aur.archlinux.org>
# Contributor: Dmitriy Morozov <archlinux@foxcub.org>
# Contributor: Larry Hajali <larryhaja [at] gmail [dot] com>

pkgname=libqglviewer-2.4-qt4
_pkgname=libQGLViewer
pkgver=2.4.0
pkgrel=1
pkgdesc="C++ library based on Qt that eases the creation of OpenGL 3D viewers (2.4 version)"
url="http://www.libqglviewer.com/"
depends=('qt4' 'glu' 'mesa')
conflicts=('libqglviewer-qt4' 'libqglviewer')
arch=('i686' 'x86_64')
license=('GPL2' 'GPL3' 'custom')
source=("http://www.libqglviewer.com/src/${_pkgname}-${pkgver}.tar.gz")
md5sums=('1f861b8c1c00364b18382877c3d2ac39')
options=(!makeflags)

build()
{
  cd ${_pkgname}-${pkgver}
  
  qmake-qt4 -o Makefile ${_pkgname}-${pkgver}.pro || return 1
  
  make \
    CFLAGS="-pipe ${CFLAGS} -D_REENTRANT -Wall -W -fPIC \$(DEFINES)" \
    CXXLIBS=" ${CXXLIBS} " \
    CXXFLAGS="-pipe ${CXXFLAGS} -I/usr/include/GL -D_REENTRANT -Wall -W -fPIC \$(DEFINES)" || return 1
    
  
}

package()
{
  cd ${_pkgname}-${pkgver}

  make install INSTALL_ROOT="$pkgdir" || return 1
  
  # Install license.
  install -d -m 0755 "${pkgdir}"/usr/share/licenses/$pkgname/ || return 1
  install -m 0644 LICENCE GPL_EXCEPTION "${pkgdir}"/usr/share/licenses/$pkgname/ || return 1
}
