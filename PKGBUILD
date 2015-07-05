# Maintainer: Dirk Berg <dberg1981@googlemail.com>

pkgname=libaacs-git
pkgver=20120408
pkgrel=1
pkgdesc="Blu-Ray aacs library"
arch=('i686' 'x86_64')
depends=()
license=('LGPL')
url="http://www.videolan.org/developers/libaacs.html"
makedepends=('git' 'flex' 'byacc')
source=()
md5sums=()
provides=('libaacs')
conflicts=('libaacs')

_gitroot="git://git.videolan.org/libaacs.git"
_gitname="libaacs"

build() {
    msg "Connecting to GIT server..."

    if [ -d ${srcdir}/$_gitname ] ; then
        cd $_gitname && git pull origin
        msg "The local files are updated."
    else
        git clone $_gitroot
    fi
    
    msg "GIT checkout done or server timeout"
    msg "Starting make..."

    cd ${srcdir}/libaacs
    ./bootstrap
    ./configure --prefix=/
    make || return 1
    make DESTDIR=${pkgdir}/usr install || return 1    
}
