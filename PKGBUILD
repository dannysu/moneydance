# Maintainer: Sander Zuidema <archlinux at grunny dot demon dot nl>
# Contributor: Lukas Grossar <lukas dot grossar at gmail dot com>

pkgname=moneydance
pkgver=2015.1220
pkgrel=1
epoch=
pkgdesc="A personal finance manager for Mac, Windows and Linux"
arch=('i686' 'x86_64')
url="http://www.moneydance.com/"
license=('custom')
groups=()
depends=('java-runtime' 'bash')
makedepends=('libicns')
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
        'moneydance.patch'
        'http://infinitekind.com/stabledl/2015/Moneydance.zip')
source_i686+=(http://infinitekind.com/stabledl/2015/Moneydance_linux_x86.tar.gz)
source_x86_64+=(http://infinitekind.com/stabledl/2015/Moneydance_linux_amd64.tar.gz)
sha256sums=('9c45324e6929c3ef52d195cfbbc6014e666b2f34a1be03c0bd81cd50b44cd89a'
            '4e48af0efb968910304767fe0bbab733aaa7b15f4d05b6a82c9fdac78351776f'
            '296df4d3ab922bf5617c25a7c7f55d2bedf3d3037b2b90a8c969d805904917b5')
sha256sums_i686=('7b8e9dfe98b0f37293a5589d78ea8c30a3b5d7239037adbb942151541068188d')
sha256sums_x86_64=('3d873a9a5fb7d846281282c9b986e71ecdbb7184f8f85c7fdf3594ec6ccb693e')

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

  # copy Mac icon since they're higher res
  cd "$srcdir/${pkgname^}.app/Contents/Resources/"
  icns2png -o . -x Moneydance.icns || return 1
  install -m644 "Moneydance_1024x1024x32.png" "$pkgdir/usr/share/pixmaps/$pkgname.png" || return 1

  cd "$srcdir/${pkgname^}"
  patch -uN "resources/moneydance.desktop" "../../moneydance.patch"
  install -m644 "resources/moneydance.desktop" "$pkgdir/usr/share/applications/$pkgname.desktop" || return 1
  install -m644 "resources/license.txt" "$pkgdir/usr/share/licenses/$pkgname/LICENSE" || return 1
  install -m644 jars/*.jar "$pkgdir/usr/share/java/$pkgname" || return 1
}
