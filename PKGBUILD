# Maintainer: Victor Levasseur <victorlevasseur52@gmail.com>
# Altered by Todor Imreorov for github <blurymind@gmail.com>


pkgname=gdevelop-git
pkgver=master
pkgrel=1
pkgdesc="A full featured, open source game development software, allowing to create HTML5 and native games without knowing a programming language. All the game logic is made thanks to an intuitive and powerful event based system."
arch=('i686' 'x86_64')
url="http://www.compilgames.net"
license=('GPL' 'MIT' 'zlib/png')
groups=()
install='gdevelop-git.install'
makedepends=('rsync' 'cmake' 'git' 'curl')
depends=('gcc' 'wxgtk' 'openal' 'p7zip' 'glew' 'libsndfile' 'systemd' 'libjpeg-turbo' 'desktop-file-utils' 'gtk-update-icon-cache')
#changelog='PKGBUILD.changelog'
source=('git+https://github.com/4ian/GD.git')
md5sums=(SKIP)

pkgver() {
   cd "$srcdir/GD"
   ver=$(git describe --abbrev=0 | sed -e 's/[^.0-9]//g')
   count=$(git rev-list --count HEAD)
   commit=$(git rev-parse --short HEAD)
   echo $ver.r$count.$commit
}

build() {
  cd "$srcdir"/GD
  cd Binaries
  rm -rf .build
  mkdir .build
  cd .build
  cmake ../..

  #Build the whole project
  make -j4
}

package() {
  cd "$srcdir"/GD
  cd Binaries/.build
  make install DESTDIR="$pkgdir"
  #Remove sfml installed libs
  rm -rf "$pkgdir"/usr/local
}
