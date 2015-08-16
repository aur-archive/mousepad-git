# Maintainer:  swanson <webaake gmail com>
# Contributor: swanson

pkgname=mousepad-git
pkgver=20140820
pkgrel=1
pkgdesc="Mousepad 0.3.0 git version"
arch=('i686' 'x86_64')
url="http://www.xfce.org/"
license=('GPL')
depends=('desktop-file-utils' 'gtk2' 'hicolor-icon-theme' 'gtksourceview3' 'exo' )
makedepends=('xfce4-dev-tools' 'git' 'pkgconfig>=0.9.0' 'gettext')
optdepends=('libgnomeprintui: for printing support')
provides=('mousepad')
conflicts=('mousepad')
install=mousepad.install
md5sums=('c9c7c6fc12dfe870a44cf25d385ab0d1')


_gitroot="git://git.xfce.org/apps/mousepad/"
_gitname="mousepad"

build() {
  cd "${srcdir}"
  msg "Connecting to GIT server...."

  if [ -d ${_gitname} ] ; then
    cd ${_gitname} && git pull origin
    msg "The local files are updated."
  else
    git clone ${_gitroot} ${_gitname}
  fi

#  msg "GIT checkout done or server timeout"
#  msg "Starting make..."

rm -rf "${srcdir}/${_gitname}-build"
git clone "${srcdir}/${_gitname}" "${srcdir}/${_gitname}-build"
cd "${srcdir}/${_gitname}-build"
export "DESTDIR=$pkgdir"
sh autogen.sh --prefix=/usr --disable-debug 
make  
}
package() {
cd "${srcdir}/${_gitname}-build"
make INSTALL_ROOT="$pkgdir" install
	}


