# Maintainer: Buce <dmbuce@gmail.com>

pkgname=blargup-git
pkgver=0.r9.g0d4ddfc
pkgver() {
  cd "$srcdir/$pkgname"
  if ! git describe --tags 2>/dev/null; then
    echo "0.r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
  fi | sed 's/-/.r/; s/-/./g'
}
pkgrel=1
pkgdesc="A simple profile-based backup script."
arch=(any)
url="https://github.com/DMBuce/blargup"
license=('BSD')
groups=()
depends=('bash')
optdepends=('rsync' 'mysql')
makedepends=('git')
provides=(blargup)
conflicts=(blargup)
replaces=()
backup=('etc/blargup/conf.d/my.cnf'
        'etc/blargup/conf.d/exclude.conf'
        'etc/blargup/systems.d/rsync-pull.sh'
        'etc/blargup/systems.d/rsync-local.sh'
        'etc/blargup/systems.d/mysql.sh'
        'etc/blargup/examples/example-profile')
options=()
install=
source=("$pkgname::git://github.com/DMBuce/blargup.git")
md5sums=('SKIP')

build() {
  cd "$srcdir/$pkgname"
  make
}

package() {
  cd "$srcdir/$pkgname"
  make prefix=/usr sysconfdir=/etc localstatedir=/var DESTDIR="$pkgdir" install

  install -D -m644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  #install -D -m644 etc/examples/example-profile "$pkgdir/etc/blargup/example-profile"
}

# vim:set ts=2 sw=2 et:
