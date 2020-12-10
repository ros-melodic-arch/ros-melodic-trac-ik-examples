# Script generated with create_pkgbuild.py
# For more information: https://github.com/ros-melodic-arch/ros-build-tools-py3
pkgdesc="ROS - This package contains the source code for testing and comparing trac_ik."
url='http://wiki.ros.org/trac_ik_examples'

pkgname='ros-melodic-trac-ik-examples'
pkgver='1.5.1'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=2
license=('BSD')

ros_makedepends=(
  ros-melodic-catkin
  ros-melodic-orocos-kdl
  ros-melodic-trac-ik-lib
)
makedepends=(
  'cmake' 'ros-build-tools'
  ${ros_makedepends[@]}
  boost1.69
)

ros_depends=(
  ros-melodic-orocos-kdl
  ros-melodic-trac-ik-lib
  ros-melodic-xacro
)

depends=(
  ${ros_depends[@]}
  boost1.69
)

_dir="traclabs-trac_ik-f4597094e974/trac_ik_examples"
source=("trac_ik-${pkgver}.tar.gz"::"https://bitbucket.org/traclabs/trac_ik/get/${pkgver}.tar.gz")
sha256sums=('67bdfb8dfcdf99c4ff5bd10de3c214527443a5c1ac54c99a0b5590d2692bf676')

build() {
   # Use ROS environment variables
   source /usr/share/ros-build-tools/clear-ros-env.sh
   [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

   # Create build directory
   [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
   cd ${srcdir}/build

   # Fix Python2/Python3 conflicts
   /usr/share/ros-build-tools/fix-python-scripts.sh -v 3 ${srcdir}/${_dir}

   # Build project
   cmake ${srcdir}/${_dir} \
     -DCMAKE_BUILD_TYPE=Release \
     -DCATKIN_BUILD_BINARY_PACKAGE=ON \
     -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
     -DPYTHON_EXECUTABLE=/usr/bin/python3 \
     -DSETUPTOOLS_DEB_LAYOUT=OFF \
		 -DBOOST_ROOT=/opt/boost1.69
   make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

