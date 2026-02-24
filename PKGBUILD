# Maintainer: Ryan De Villa (ryandv) <general@ryandv.me>

pkgname=onnxruntime-genai
pkgver=0.12.0
pkgrel=2
pkgdesc="Microsoft's Generative AI extensions for onnxruntime"
arch=('any')
url="https://github.com/microsoft/onnxruntime-genai"
license=('MIT')
depends=('python' 'onnxruntime-cpu')
makedepends=('git' 'cmake' 'python' 'python-pip' 'python-requests' 'python-build' 'python-installer' 'python-wheel')
source=("${url}/archive/refs/tags/v${pkgver}.tar.gz")
md5sums=('376ff486fc8ad639ec040b1fc7524b66')

build() {
    cd "${pkgname}-${pkgver}"

    CFLAGS='-I/usr/include/onnxruntime/' CXXFLAGS='-I/usr/include/onnxruntime/' python build.py --config Release --skip_tests
}

package() {
    cd "${pkgname}-${pkgver}"

    CFLAGS='-I/usr/include/onnxruntime/' CXXFLAGS='-I/usr/include/onnxruntime/' python -m installer --destdir="$pkgdir" build/Linux/Release/wheel/*.whl

    install -Dm644 src/ort_genai.h "$pkgdir/usr/include/onnxruntime/ort_genai.h"
    install -Dm644 src/ort_genai_c.h "$pkgdir/usr/include/onnxruntime/ort_genai_c.h"
}
