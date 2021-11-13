# Maintainer: Atom Long <atom.long@hotmail.com>

_pkgname="gh-hosts"
pkgname="gh-hosts-git"
pkgver=20211113
pkgrel=1
pkgdesc="Adding GitHub IPs to hosts"
arch=('any')
url="https://github.com/atomlong/github-hosts"
license=('custom')
makedepends=('go>=1.17')
options=(!lto)
conflicts=('gh-hosts')
provides=('gh-hosts')
source=("gh-hosts::git+${url}.git")
sha256sums=("SKIP")

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
  install -D -m755 gh-hosts "${pkgdir}/usr/bin/gh-hosts"
}
