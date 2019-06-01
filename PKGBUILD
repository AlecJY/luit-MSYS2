pkgname=luit
pkgver=20190106
pkgrel=2
pkgdesc="Luit is a filter that can be run between an arbitrary application and a UTF-8 terminal emulator."
arch=('i686' 'x86_64')
url='https://invisible-island.net/luit/luit.html'
license=('BSD')
source=("ftp://ftp.invisible-island.net/luit/luit-${pkgver}.tgz"
        "fix-ldflags.patch")
depends=('gcc-libs' 'libiconv' 'zlib')
makedepends=('diffutils' 'gcc' 'libiconv-devel' 'make' 'patch' 'zlib-devel')
sha256sums=('2b900f65ccdc38f8bfc11c6020069d055ba63fce6f90baefe8efc222a5ca3920'
            'b2384d6801841d30830354c0806356be993ff86e9c8f1dfdca80a1de011da981')

prepare() {
    cd "${srcdir}/luit-${pkgver}"
    patch -p0 -i "${srcdir}/fix-ldflags.patch"
}

build() {
    cd "${srcdir}/luit-${pkgver}"
    ./configure --prefix=/usr 
    make
}

package() {
    cd "${srcdir}/luit-${pkgver}"
    make DESTDIR="${pkgdir}" install

    install -Dm644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/COPYING"
}
