# Script generated with Bloom
pkgdesc="ROS - ardrone_autonomy is a ROS driver for Parrot AR-Drone 1.0 and 2.0 quadrocopters. This driver is based on official AR-Drone SDK version 2.0.1."
url='http://wiki.ros.org/ardrone_autonomy'

pkgname='ros-kinetic-ardrone-autonomy'
pkgver='1.4.1_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('binutils'
'daemontools'
'git'
'gtk2'
'iw'
'libxml2'
'ros-kinetic-camera-info-manager'
'ros-kinetic-catkin'
'ros-kinetic-image-transport'
'ros-kinetic-message-generation'
'ros-kinetic-nav-msgs'
'ros-kinetic-roscpp'
'ros-kinetic-roslint'
'ros-kinetic-sensor-msgs'
'ros-kinetic-std-srvs'
'ros-kinetic-tf'
'sdl'
'systemd'
)

depends=('ros-kinetic-camera-info-manager'
'ros-kinetic-image-transport'
'ros-kinetic-message-runtime'
'ros-kinetic-nav-msgs'
'ros-kinetic-roscpp'
'ros-kinetic-sensor-msgs'
'ros-kinetic-std-srvs'
'ros-kinetic-tf'
)

conflicts=()
replaces=()

_dir=ardrone_autonomy
source=()
md5sums=()

prepare() {
    cp -R $startdir/ardrone_autonomy $srcdir/ardrone_autonomy
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

