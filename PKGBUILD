# Maintainer: Robert Orzanna <orschiro@gmail.com>"

pkgname='prezi-desktop'
pkgver=3.091
license=('custom')
pkgrel=1
arch=('i686' 'x86_64')
pkgdesc="Prezi Desktop is a presentation software giving you all the power of Prezi without needing an internet connection."
url=('https://prezi.com/desktop/')
source=("http://cdn01.prezi.com/prezi/desktop/PreziDesktop_3.091.air" 'prezi-desktop.desktop')
noextract=("PreziDesktop_$pkgver.air")
conflicts=('prezi-desktop4')
depends=('bash' 'adobe-air-sdk' 'unzip')
md5sums=('6cb85fe0ec6ea727862cd32d50d5d7df'
         'cd029f5631f04da850822143753f5d65')

package() {
  cd "${srcdir}"
  mkdir "${pkgdir}"/opt/
  mkdir "${pkgdir}"/opt/airapps
  mkdir "${pkgdir}"/usr/
  mkdir "${pkgdir}"/usr/bin
  install "${srcdir}"/PreziDesktop_$pkgver.air  "${pkgdir}"/opt/airapps/prezi-desktop.air
  mkdir "${pkgdir}"/opt/airapps/prezi-desktop
  cd "${pkgdir}"/opt/airapps/prezi-desktop
  unzip ../prezi-desktop.air
  echo "#!/bin/bash" >>"${pkgdir}"/usr/bin/prezi-desktop
  echo "/opt/adobe-air-sdk/bin/adl -nodebug /opt/airapps/prezi-desktop/META-INF/AIR/application.xml /opt/airapps/prezi-desktop/" >> "${pkgdir}"/usr/bin/prezi-desktop
  chmod +x "${pkgdir}"/usr/bin/prezi-desktop
  mkdir -p "${pkgdir}"/usr/share/applications
  install "${srcdir}"/${pkgname}.desktop "${pkgdir}"/usr/share/applications/ 
}