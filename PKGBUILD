# Maintainer: Atom Long <atom.long@hotmail.com>

_pkgname="gh-hosts"
pkgname="gh-hosts-git"
pkgver=20211113
pkgrel=3
pkgdesc="Adding GitHub IPs to hosts"
arch=('any')
url="https://github.com/atomlong/github-hosts"
license=('custom')
makedepends=('go>=1.17')
options=(!lto)
conflicts=("${_pkgname}")
provides=("${_pkgname}")
source=("${_pkgname}::git+${url}.git"
        "${_pkgname}.service"
        "${_pkgname}.timer")
sha256sums=("SKIP"
            "f05786c4154cf329dc51005ae43262f5a6acbea4c3b76eb417b6e8e52ed1c178"
            "870c705f5bd28ae4d7f8e5d432cbdc0f39bc61c67ae179d31cd0d953c97ee308")

pkgver() {
  cd "$srcdir/$_pkgname"
  git show -s --format="%ci" HEAD | sed -e 's/-//g' -e 's/ .*//'
}

build() {
  cd "$srcdir/$_pkgname"
  export GOPATH="$srcdir"/gopath
  go build -o gh-hosts
}

package() {
  cd "$srcdir/$_pkgname"
  install="${_pkgname}.install"
  install -D -m755 gh-hosts "${pkgdir}/usr/bin/gh-hosts"
  install -Dm644 ../${_pkgname}.service ${pkgdir}/usr/lib/systemd/system/${_pkgname}.service
  install -Dm644 ../${_pkgname}.timer ${pkgdir}/usr/lib/systemd/system/${_pkgname}.timer
}
