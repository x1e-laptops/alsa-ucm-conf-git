# Maintainer: Reza Jahanbakhshi <reza.jahanbakhshi at gmail dot com>

pkgname=alsa-ucm-conf-git
pkgbasename="${pkgname%-git}"
pkgver=1.2.14.1e5f874
pkgrel=2
pkgdesc="ALSA Use Case Manager configuration (and topologies), git version"
provides=("${pkgbasename}")
conflicts=("${pkgbasename}")
arch=(any)
url="https://alsa-project.org/"
license=(BSD)
source=("https://github.com/alsa-project/alsa-ucm-conf/archive/1e5f874de71844d559074ad1bc6c9f224825b442.tar.gz")
sha512sums=('SKIP')
b2sums=('SKIP')

_srcname=${pkgbasename}-1e5f874de71844d559074ad1bc6c9f224825b442

prepare() {
  local _patchfile
  for _patchfile in "${source[@]}"; do
    _patchfile="${_patchfile%%::*}"
    _patchfile="${_patchfile##*/}"
    [[ $_patchfile = *.patch ]] || continue
    echo "Applying patch $_patchfile..."
    patch --directory="${pkgbasename}" --forward --strip=1 --input="${srcdir}/${_patchfile}"
  done
}

package() {
  cd $srcdir/$_srcname
  install -vdm 755 "${pkgdir}/usr/share/alsa/"
  cp -av ucm2 "${pkgdir}/usr/share/alsa/"
  install -vDm 644 LICENSE -t "$pkgdir/usr/share/licenses/$pkgbasename"
  install -vDm 644 README.md -t "$pkgdir/usr/share/doc/$pkgbasename"
  install -vDm 644 ucm2/README.md -t "$pkgdir/usr/share/doc/$pkgbasename/ucm2"
}

