# Contributor: Pável Varela Rodríguez [NeOnsKuLL] <neonskull@gmail.com>
pkgname=obmenugen
pkgver=0.5
pkgrel=3
_serie=0.5
_pkgrev=72
pkgdesc="Menu generator for Openbox3, based on .desktop files"
url="https://launchpad.net/obmenugen"
arch=('i686' 'x86_64')
license=('GPL')
depends=(openbox)
conflicts=(obmenugen-bin)
makedepends=(dmd1 libphobos1 txt2tags)
options=('!strip' 'docs')
source=(http://launchpad.net/obmenugen/$_serie/$pkgver/+download/obmenugen-$pkgver-r$_pkgrev.tar.bz2 makefile.patch)
md5sums=(c28dd7c12044062e50792f8edd0365c2 837015de87f91f5d43845d1fd500282e)

[ "$CARCH" = "x86_64" ] && depends=(${depends[@]} lib32-glibc)
[ "$CARCH" = "x86_64" ] && makedepends=(lib32-dmd txt2tags)

[[ -n "$(which gdmd 2>/dev/null)" ]] &&  makedepends=(gdc-bin txt2tags)

build() {
  cd $srcdir/obmenugen-$pkgver-r$_pkgrev
  patch -p1 < $startdir/makefile.patch
  CC=""
  [[ -n $(which gdmd 2>/dev/null) ]] && CC="CC=gdmd" 
  make $CC || return 1
  make install PREFIX=$pkgdir/usr/ || return 1
}

