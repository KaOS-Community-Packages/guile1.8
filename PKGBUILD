pkgname=guile1.8
pkgver=1.8.8
pkgrel=8
pkgdesc='Portable, embeddable Scheme implementation written in C. Legacy branch.'
url="https://www.gnu.org/software/guile/"
arch=('x86_64')
license=('GPL')
depends=('gmp' 'libltdl' 'ncurses>=5.7' 'texinfo')
source=(https://ftp.gnu.org/pub/gnu/guile/guile-$pkgver.tar.gz)
md5sums=('18661a8fdfef13e2fcb7651720aa53f3')

build() {
  cd guile-$pkgver
  export CFLAGS+=" -O1"
  ./configure --prefix=/usr \
	--disable-static  \
	--disable-error-on-warning \
        --program-suffix=1.8
  make LDFLAGS+="-lpthread"
}

package() {
  cd guile-$pkgver
  make DESTDIR="$pkgdir" install
  
  rm -rf "$pkgdir"/usr/share/info
  sed -i '1s/guile/guile1.8/' -i "$pkgdir"/usr/bin/guile-config1.8
  mv "$pkgdir"/usr/share/aclocal/guile.m4 "$pkgdir"/usr/share/aclocal/guile18.m4
}
