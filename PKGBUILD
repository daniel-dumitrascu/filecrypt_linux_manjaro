# PKGBUILD
# Maintainer: daniel.dumitrascu.dev@gmail.com

pkgname=filecrypt
pkgver=1.0
pkgrel=1
pkgdesc="Easy encrypt and decrypt files using the mouse context menu"
arch=('x86_64')
url="https://github.com/daniel-dumitrascu/filecrypt"
license=("MIT")
makedepends=('git')
source=('filecrypt.tar.gz')
md5sums=('SKIP')

_server_app_name="filecrypt_server"
_client_app_name="filecrypt_client"
_script_name="filecrypt.py"

build() {
  cd "$pkgname"/server
  go build

  cd ../client
  go build
}

package() {
  cd "$pkgname"/server
  install -Dm755 ./server "$pkgdir/usr/bin/$_server_app_name"
  
  cd ../client
  install -Dm755 ./client "$pkgdir/usr/bin/$_client_app_name"

  cd ../server/scripts
  cp "$_script_name" "$pkgdir"/usr/bin/"$_script_name"
}
