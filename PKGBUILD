##This is a basic PKGBUILD for rdis to ease building RDIS in my Arch boxes
##Maintainer : TDKPS
pkgname=rdis-lua
pkgrel=1
pkgver=20121230
arch=(x86_64)
url="https://github.com/endeav0r/rdis-lua"
license=('GPLv3')
depends=(gtk3 luajit cairo jansson git lua51-socket rdis)
_gitroot="https://github.com/endeav0r/rdis-lua.git"
_gitname="rdis-lua"

#define user
user=root

build() {

  #define folder placement variable
  where=/$user/rdis-lua
  cd "$srcdir"

  msg "Connecting to GIT server..."
  if [[ -d ${_gitname} ]]; then
    (cd ${_gitname} && git pull origin)
  else
    git clone ${_gitroot} ${_gitname}
  fi

  msg "GIT checkout done or server timeout"
  msg "Creating rdis-lua directory in $where"

  mkdir $where
  cp $srcdir/rdis-lua/* $where
  rm -r $srcdir

  echo "File copying done." 

  #PATH_TO_RDIS_LUA = $where
  
  echo "local PATH_TO_RDIS_LUA = '$where'
  package.path = package.path .. ';' .. $where .. '/?.lua'
  dofile($where .. '/rdis.lua')" >/$user/.rdis.conf

  echo "Complete"

  }