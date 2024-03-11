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
depends=('go')
install=service.install

_server_app_name="filecrypt_server"
_client_app_name="filecrypt_client"
_script_name="filecrypt.py"
_service_name="filecrypt.service"

prepare() {
    git clone --depth=1 --branch=main https://github.com/daniel-dumitrascu/filecrypt.git "$pkgname"
}

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

  cd ../server/daemon
  install -Dm755 ./"$_service_name" "$pkgdir/etc/systemd/system/$_service_name"

  cd ../scripts
  cp "$_script_name" "$pkgdir"/usr/bin/"$_script_name"

  cd $HOME
  mkdir -p ".$pkgname"
}
