# Script generated with Bloom
pkgdesc="ROS - A full, but simple robot drive system. Includes skid steering joystick teleoperation, control of a panning servo, a cmd_vel multiplexer, and Arduino firmware."
url='http://wiki.ros.org/simple_drive'

pkgname='ros-kinetic-simple-drive'
pkgver='0.1.0_1'
pkgrel=1
arch=('any')
license=('Unlicense'
)

makedepends=('ros-kinetic-actionlib-msgs'
'ros-kinetic-catkin'
'ros-kinetic-geometry-msgs'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
'ros-kinetic-std-msgs'
)

depends=('ros-kinetic-actionlib-msgs'
'ros-kinetic-geometry-msgs'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
'ros-kinetic-std-msgs'
)

conflicts=()
replaces=()

_dir=simple_drive
source=()
md5sums=()

prepare() {
    cp -R $startdir/simple_drive $srcdir/simple_drive
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

