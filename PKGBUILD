# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - A 2D navigation stack that takes in information from odometry, sensor streams, and a goal pose and outputs safe velocity commands that are sent to a mobile base."
url='http://wiki.ros.org/navigation'

pkgname='ros-hydro-navigation'
pkgver='1.11.11'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD,LGPL,LGPL (amcl)')

ros_makedepends=(ros-hydro-catkin)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-carrot-planner
  ros-hydro-rotate-recovery
  ros-hydro-map-server
  ros-hydro-fake-localization
  ros-hydro-move-slow-and-clear
  ros-hydro-base-local-planner
  ros-hydro-move-base-msgs
  ros-hydro-move-base
  ros-hydro-dwa-local-planner
  ros-hydro-costmap-2d
  ros-hydro-nav-core
  ros-hydro-navfn
  ros-hydro-clear-costmap-recovery
  ros-hydro-robot-pose-ekf
  ros-hydro-voxel-grid
  ros-hydro-amcl)
depends=(${ros_depends[@]})

_tag=release/hydro/navigation/${pkgver}-${_pkgver_patch}
_dir=navigation
source=("${_dir}"::"git+https://github.com/ros-gbp/navigation-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
