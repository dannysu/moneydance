# Maintainer: Sander Zuidema <archlinux at grunny dot demon dot nl>
# Contributor: Lukas Grossar <lukas dot grossar at gmail dot com>

pkgname=moneydance
pkgver=2015.1175
pkgrel=1
epoch=
pkgdesc="A personal finance manager for Mac, Windows and Linux"
arch=('i686' 'x86_64')
url="http://www.moneydance.com/"
license=('custom')
groups=()
depends=('java-runtime' 'bash')
makedepends=()
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=('moneydance.sh'
        'moneydance.patch')
source_i686+=(http://infinitekind.com/stabledl/2015/Moneydance_linux_x86.tar.gz)
source_x86_64+=(http://infinitekind.com/stabledl/2015/Moneydance_linux_amd64.tar.gz)
sha256sums=('9c45324e6929c3ef52d195cfbbc6014e666b2f34a1be03c0bd81cd50b44cd89a'
            '4e48af0efb968910304767fe0bbab733aaa7b15f4d05b6a82c9fdac78351776f')
sha256sums_i686=('43d092969935e122a3a136c387cb0326e0543a0f7ca6ada84944fec56051702c')
sha256sums_x86_64=('568d4565ef9ac25a65eec4b0769889dab46931d722943cc5f601b2aeda7d001d')

package() {
  # generate directories in $pkgdir
  install -m755 -d "$pkgdir/usr/bin" \
    "$pkgdir/usr/share/java/$pkgname" \
    "$pkgdir/usr/share/licenses/$pkgname" \
    "$pkgdir/usr/share/applications" \
    "$pkgdir/usr/share/pixmaps"

  # copy files
  cd "$srcdir"
  install -m755 "$pkgname.sh" "$pkgdir/usr/bin/$pkgname" || return 1
  cd "$srcdir/${pkgname^}"
  patch -uN "resources/moneydance.desktop" "../../moneydance.patch"
  install -m644 "resources/moneydance.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop" || return 1
  install -m644 "resources/license.txt" "$pkgdir/usr/share/licenses/$pkgname/LICENSE" || return 1
  install -m644 "resources/moneydance_icon32.png" "$pkgdir/usr/share/pixmaps/$pkgname.png" || return 1
  install -m644 jars/*.jar "$pkgdir/usr/share/java/$pkgname" || return 1
}
