# Maintainer: Yaff Are <yaffareATgmail.com>
# Contributor: Yaff Are <yaffareATgmail.com>

pkgname=systemd-shell-wrapper
pkgver=20130109
pkgrel=1
pkgdesc="Simple shell wrapper script around the systemd ctls, cloning rc.d output"
arch=(any)
url="https://github.com/yaffare/systemd-shell-wrapper"
license=('WTFPL')
depends=('bash')
optdepends=()
makedepends=('git')
conflicts=()
provides=()
replaces=()
backup=('etc/systemd/shell-wrapper.conf')
source=()
install=${pkgname}.install
sha256sums=()
 
_gitroot="git://github.com/yaffare/systemd-shell-wrapper.git"
_gitname="systemd-shell-wrapper"

build() {

    cd ${srcdir}
    msg "Connecting to github.com GIT server...."

    if [ -d ${srcdir}/$_gitname ] ; then
        cd $_gitname && git pull origin
        msg "The local files are updated."
    else
        git clone $_gitroot
    fi

    msg "GIT checkout done or server timeout"
    msg "Starting script install..."

    git clone ${srcdir}/$_gitname ${srcdir}/$_gitname-build
    cd ${srcdir}/$_gitname-build
    
    install -D -m 644 "shell-wrapper.conf" "$pkgdir/etc/systemd/shell-wrapper.conf"
    install -D -m 755 "systemd-shell-wrapper.bash" "$pkgdir/etc/profile.d/systemd-shell-wrapper.bash"
    install -D -m 755 "systemd-shell-wrapper.sh" "$pkgdir/etc/profile.d/systemd-shell-wrapper.sh"
}
