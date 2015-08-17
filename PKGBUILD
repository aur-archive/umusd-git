#Contributor <Themaister> <maister@archlinux.us>

pkgname=umusd-git
pkgver=20120603
pkgrel=1
pkgdesc="Very simple audio player based on FFmpeg with GTK+ frontend."

url="http://github.com/Themaister/umusd"
arch=('i686' 'x86_64')

license=('GPL')
depends=('ffmpeg' 'gtkmm' 'alsa-lib')
makedepends=('git')

_gitroot="git://github.com/Themaister/umusd.git"
_gitname="umusd"

build() 
{
   cd $srcdir

   msg "Cloning uMusD from GIT"
   if [ -d $_gitname ]; then
      cd $_gitname
      git pull || return 1
   else
      git clone $_gitroot $_gitname || return 1
      cd $_gitname
   fi

   make
   cd gtk
   make
}

package()
{
   mkdir -p $pkgdir/usr/bin
   mkdir -p $pkgdir/usr/share/{icons,applications}
   cd $srcdir/$_gitname
   make install PREFIX=$pkgdir/usr
   cd gtk
   make install PREFIX=$pkgdir/usr
}


