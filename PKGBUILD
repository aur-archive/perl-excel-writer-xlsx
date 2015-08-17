pkgname='perl-excel-writer-xlsx'
pkgver='0.49'
pkgrel='1'
pkgdesc="Excel::Writer::XLSX - Create a new file in the Excel 2007+ XLSX format."
arch=('any')
license=('PerlArtistic' 'GPL')
options=('!emptydirs')
depends=('perl' 'perl-archive-zip')
makedepends=()
url='http://search.cpan.org/perldoc?Excel%3A%3AWriter%3A%3AXLSX'
source=("http://search.cpan.org/CPAN/authors/id/J/JM/JMCNAMARA/Excel-Writer-XLSX-${pkgver}.tar.gz")
md5sums=('3fe662dcfa5e30627ff0f06dafbfc823')

build() {
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""                 \
      PERL_AUTOINSTALL=--skipdeps                            \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'"     \
      PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
      MODULEBUILDRC=/dev/null

    cd "${srcdir}/Excel-Writer-XLSX-$pkgver" 
    /usr/bin/perl Makefile.PL
    make
  )
}

check() {
  cd "${srcdir}/Excel-Writer-XLSX-$pkgver"
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""
    make test
  )
}

package() {
  cd "${srcdir}/Excel-Writer-XLSX-$pkgver"
  make install
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}

