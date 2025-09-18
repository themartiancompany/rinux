# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
#   Jan Alexander Steffens (heftig)
#     <heftig@archlinux.org>

_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_docs" ]]; then
  _docs="false"
fi
_py="python"
_pkg=linux
pkgbase="${_pkg}"
pkgver="6.15.3.arch1"
pkgrel=1
_pkgdesc=(
  'The Linux kernel.'
)
pkgdesc="${_pkgdesc[*]}"
_http="https://github.com"
_ns="archlinux"
url="${_http}/${_ns}/${_pkg}"
arch=(
  'i686'
  'powerpc'
  'x86_64'
)
license=(
  'GPL-2.0-only'
)
makedepends=(
  "bc"
  "cpio"
  "gettext"
  "libelf"
  "pahole"
  "perl"
  "${_py}"
  "rust"
  "rust-bindgen"
  "rust-src"
  "tar"
  "xz"
)
if [[ "${_docs}" == "true" ]]; then
  makedepends+=(
    # htmldocs
    "graphviz"
    "imagemagick"
    "${_py}-sphinx"
    "${_py}-yaml"
    "texlive-latexextra"
  )
fi
options=(
  "!debug"
  "!strip"
)
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_sig_ns="${_evmfs_ns}"
# https://www.kernel.org/pub/linux/kernel/v6.x/sha256sums.asc
_sum='12b50c89925438d9cd7385a0cafc9c433e6562ac5df00a21889fce9f548d65b0'
# Kernel.org
_sig_sum="658b804170201b5457e50c779f2cd6605889a58d2bc852f4458f85f0590a2e01"
# The Martian Company
_sig_sum="ede44158ff30c94c7e8cee273d691a73dd96cb9fce7f16afc7f93167eae4bd7b"
_patch_sum='70f591ba14be9789caa2affc5a5f9e404f9753ecd7ae1ef2fcbafeb285f590dd'
# Steffen signature
_patch_sig_sum="fad84783de28bf0a23392e8da658d86a9ff1642e089fda2eb70a2990776068b9"
# Dvorak signature
_patch_sig_sum="27766c44569b6dda1211d3fab256e696c4da718b88fd8515ec596500ac291323"
_config_sum='eed83e8a6c1524a7ad7e5d836cc6d7fa291b7c8e205dd7dd68dffaae22b77812'
_chain_id="100"
_fs="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_srctag="v${pkgver%.*}-${pkgver##*.}"
_tag_name="pkgver"
_tag="${_srctag}"
_srcname="${_pkg}-${pkgver%.*}"
_tarname="${_srcname}"
_patchname="${_pkg}-${_tag}.patch"
_domain="https://cdn.kernel.org"
_http_archive_dir="https://cdn.${_domain}/pub/${_pkg}/kernel"
_http_uri="${_http_archive_dir}/v${pkgver%%.*}.x/${_tarname}.tar.xz"
_http_sig_uri="${_http_archive_dir}/v${pkgver%%.*}.x/${_srcname}.tar.sign"
_http_src="${_tarname}.tar.xz::${_http_uri}"
_http_sig_src="${_tarname}.tar.sign::${_http_sig_uri}"
_http_patch_dir="${url}/releases/download"
_http_patch_uri="${_http_patch_dir}/${_tag}/${_patchname}.zst"
_http_patch_sig_uri="${_http_patch_uri}.sig"
_http_patch_src="${_tarname}.tar.sign::${_http_sig_uri}"
_http_patch_sig_uri="${_http_patch_uri}.sig"
_http_patch_src="${_patchname}.zst::${_http_patch_uri}"
_http_patch_sig_src="${_patchname}.zst.sig::${_http_patch_sig_uri}"
_evmfs_dir="evmfs://${_chain_id}/${_fs}/${_evmfs_ns}"
_evmfs_sig_dir="evmfs://${_chain_id}/${_fs}/${_evmfs_sig_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_sig_uri="${_evmfs_sig_dir}/${_sig_sum}"
_evmfs_patch_uri="${_evmfs_dir}/${_patch_sum}"
_evmfs_patch_sig_uri="${_evmfs_sig_dir}/${_patch_sig_sum}"
_patch_uri=""
source=()
sha256sums=()
if [[ "${_evmfs}" == "true" ]]; then
  _src="${_tarname}.tar.xz::${_evmfs_uri}"
  _patch_src="${_patchname}.zst::${_evmfs_patch_uri}"
  _sig_src="${_tarname}.tar.xz.sig::${_evmfs_sig_uri}"
  _patch_sig_src="${_patchname}.zst.sig::${_evmfs_patch_sig_uri}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_git}" == "false" ]]; then
  _src="${_http_src}"
  _sig_src="${_http_sig_src}"
  _patch_src="${_patchname}.zst::${_http_patch_uri}"
  _patch_sig_src="${_patchname}.zst.sig::${_http_patch_sig_uri}"
fi
source+=(
  "${_src}"
  "${_sig_src}"
  "${_patch_src}"
  "${_patch_sig_src}"
  # the main kernel config file
  "config"
)
sha256sums+=(
  "${_sum}"
  "${_sig_sum}"
  "${_patch_sum}"
  "${_patch_sig_sum}"
  "${_config_sum}"
)
validpgpkeys=(
  # Linus Torvalds
  "ABAF11C65A2970B130ABE3C479BE3E4300411886"
  # Greg Kroah-Hartman
  "647F28654894E3BD457199BE38DBBDC86092693E"
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
  # Jan Alexander Steffens (heftig)
  "83BC8889351B5DEBBB68416EB8AC08600F108CDF"
)

export \
  KBUILD_BUILD_HOST="archlinux" \
  KBUILD_BUILD_USER="${pkgbase}" \
  KBUILD_BUILD_TIMESTAMP="$( \
  date \
    -Ru"${SOURCE_DATE_EPOCH:+d \
    @$SOURCE_DATE_EPOCH}")"

prepare() {
  local \
    src
  cd \
    "${_tarname}"
  echo \
    "Setting version..."
  echo \
    "-$pkgrel" > \
    "localversion.10-pkgrel"
  echo \
    "${pkgbase#linux}" > \
    "localversion.20-pkgname"
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    src="${src%.zst}"
    [[ "${src}" = *.patch ]] || \
    continue
    echo \
      "Applying patch ${src}..."
    patch \
      -Np1 < \
      "../${src}"
  done
  echo \
    "Setting config..."
  cp \
    "../config" \
    ".config"
  make \
    olddefconfig
  diff \
    -u \
    "../config" \
    ".config" || :
  make \
    -s \
    kernelrelease > \
    "version"
  cp \
    "version" \
    "${srcdir}/version"
  echo \
    "Prepared ${pkgbase} version $(<"version")."
}

build() {
  cd \
    "${_tarname}"
  make \
    all
  make \
    -C \
      "tools/bpf/bpftool" \
    "vmlinux.h" \
    feature-clang-bpf-co-re=1
  if [[ "${_docs}" == "true" ]]; then
    make \
      htmldocs
  fi
}

_package() {
  local \
    modulesdir
  cd \
    "${_tarname}"
  modulesdir="${pkgdir}/usr/lib/modules/$(<"version")"
  _pkgdesc=(
    "The Linux kernel and modules."
  )
  pkgdesc="${_pkgdesc[*]}"
  depends=(
    "coreutils"
    "initramfs"
    "kmod"
  )
  optdepends=(
    'linux-firmware: Firmware images needed for some devices.'
    'scx-scheds: To use sched-ext schedulers.'
    'wireless-regdb: To set the correct wireless channels of your country.'
  )
  provides=(
    "KSMBD-MODULE"
    "NTSYNC-MODULE"
    "VIRTUALBOX-GUEST-MODULES"
    "WIREGUARD-MODULE"
  )
  replaces=(
    "virtualbox-guest-modules-arch"
    "wireguard-arch"
  )
  echo \
    "Installing boot image..."
  # systemd expects to find the kernel
  # here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install \
    -vDm644 \
    "$(make \
         -s \
         image_name)" \
    "${modulesdir}/vmlinuz"
  # Used by mkinitcpio to name the kernel
  echo \
    "${pkgbase}" | \
    install \
      -vDm644 \
      "/dev/stdin" \
      "${modulesdir}/pkgbase"
  echo \
    "Installing modules..."
  ZSTD_CLEVEL=19 \
  # Suppress depmod
  make \
    INSTALL_MOD_PATH="${pkgdir}/usr" \
    INSTALL_MOD_STRIP=1 \
    DEPMOD="/doesnt/exist" \
    modules_install  
  # remove build link
  rm \
    "${modulesdir}/build"
}

_package-headers() {
  local \
    arch \
    builddir \
    file
  cd \
    "${_tarname}"
  builddir="${pkgdir}/usr/lib/modules/$(<"version")/build"
  _pkgdesc=(
    "Headers and scripts for"
    "building modules for the"
    "Linux kernel."
  )
  pkgdesc="${_pkg[*]}"
  depends=(
    "pahole"
  )
  echo \
    "Installing build files..."
  install \
    -vDt \
    "${builddir}" \
    -m644 \
    ".config" \
    "Makefile" \
    "Module.symvers" \
    "System.map" \
    "localversion."* \
    "version" \
    "vmlinux" \
    "tools/bpf/bpftool/vmlinux.h"
  install \
    -vDt \
    "${builddir}/kernel" \
    -m644 \
    "kernel/Makefile"
  install \
    -vDt \
    "${builddir}/arch/x86" \
    -m644 \
    "arch/x86/Makefile"
  cp \
    -t \
    "${builddir}" \
    -a \
    "scripts"
  ln \
    -srt \
    "${builddir}" \
    "${builddir}/scripts/gdb/vmlinux-gdb.py"
  # required when STACK_VALIDATION is enabled
  install \
    -vDt \
    "${builddir}/tools/objtool" \
    "tools/objtool/objtool"
  # required when DEBUG_INFO_BTF_MODULES is enabled
  install \
    -vDt \
    "${builddir}/tools/bpf/resolve_btfids" \
    "tools/bpf/resolve_btfids/resolve_btfids"
  echo \
    "Installing headers..."
  cp \
    -t \
    "${builddir}" \
    -a \
    "include"
  cp \
    -t \
    "${builddir}/arch/x86" \
    -a \
    "arch/x86/include"
  install \
    -vDt \
    "${builddir}/arch/x86/kernel" \
    -m644 \
    "arch/x86/kernel/asm-offsets.s"
  install \
    -vDt \
    "${builddir}/drivers/md" \
    -m644 \
    "drivers/md/"*".h"
  install \
    -vDt \
    "${builddir}/net/mac80211" \
    -m644 \
    "net/mac80211/"*".h"
  # https://bugs.archlinux.org/task/13146
  install \
    -vDt \
    "${builddir}/drivers/media/i2c" \
    -m644 \
    "drivers/media/i2c/msp3400-driver.h"
  # https://bugs.archlinux.org/task/20402
  install \
    -vDt \
    "${builddir}/drivers/media/usb/dvb-usb" \
    -m644 \
    "drivers/media/usb/dvb-usb/"*".h"
  install \
    -vDt \
    "${builddir}/drivers/media/dvb-frontends" \
    -m644 \
    "drivers/media/dvb-frontends/"*".h"
  install \
    -vDt \
    "${builddir}/drivers/media/tuners" \
    -m644 \
    "drivers/media/tuners/"*".h"
  # https://bugs.archlinux.org/task/71392
  install \
    -vDt \
    "${builddir}/drivers/iio/common/hid-sensors" \
    -m644 \
    "drivers/iio/common/hid-sensors/"*".h"
  echo \
    "Installing KConfig files..."
  find \
    "." \
    -name \
      'Kconfig*' \
    -exec \
      install \
      -vDm644 \
      {} \
      "${builddir}/{}" \;
  echo \
    "Installing Rust files..."
  install \
    -vDt \
    "${builddir}/rust" \
    -m644 \
    "rust/"*".rmeta"
  install \
    -vDt \
    "${builddir}/rust" \
    "rust/"*".so"
  echo \
    "Installing unstripped VDSO..."
  make \
    INSTALL_MOD_PATH="${pkgdir}/usr" \
    vdso_install \
    link=  # Suppress build-id symlinks
  echo \
    "Removing unneeded architectures..."
  for arch in "${builddir}/arch/"*"/"; do
    [[ ${arch} = *"/x86/" ]] && \
    continue
    echo \
      "Removing $(basename \
                    "${arch}")."
    rm \
      -r \
      "${arch}"
  done
  echo \
    "Removing documentation..."
  rm \
    -rf \
    "$builddir/Documentation" || \
    true
  echo \
    "Removing broken symlinks..."
  find \
    -L \
    "${builddir}" \
    -type \
      "l" \
    -printf \
      'Removing %P\n' \
    -delete
  echo \
    "Removing loose objects..."
  find \
    "${builddir}" \
    -type \
      "f" \
    -name \
      '*.o' \
    -printf \
      'Removing %P\n' \
      -delete
  echo \
    "Stripping build tools..."
  while read -rd '' file; do
    case "$(file \
              -Sib \
              "${file}")" in
      # Libraries (.so)
      application/x-sharedlib\;*)
        strip \
          -v \
            ${STRIP_SHARED} \
            "${file}" ;;
      # Libraries (.a)
      application/x-archive\;*)
        strip \
          -v \
          ${STRIP_STATIC} \
          "${file}" ;;
      # Binaries
      application/x-executable\;*)
        strip \
          -v \
          ${STRIP_BINARIES} \
          "${file}" ;;
      # Relocatable binaries
      application/x-pie-executable\;*)
        strip \
          -v \
          $STRIP_SHARED \
          "${file}" ;;
    esac
  done < <(find \
             "${builddir}" \
             -type \
               "f" \
             -perm \
               -u+x \
           ! -name \
               "vmlinux" \
             -print0)
  echo \
    "Stripping vmlinux..."
  strip \
    -v \
    $STRIP_STATIC \
    "${builddir}/vmlinux"
  echo \
    "Adding symlink..."
  mkdir \
    -p \
    "${pkgdir}/usr/src"
  ln \
    -sr \
    "${builddir}" \
    "${pkgdir}/usr/src/${pkgbase}" || \
  true
}

_package-docs() {
  local \
    builddir \
    _dst \
    _src
  cd \
    "${_tarname}"
  builddir="${pkgdir}/usr/lib/modules/$(<"version")/build"
  _pkgdesc=(
    "Documentation for the Linux kernel."
  )
  pkgdesc="${_pkgdesc[*]}"
  echo \
    "Installing documentation..."
  while read -rd '' src; do
    _dst="${_src#Documentation/}"
    _dst="$builddir/Documentation/${_dst#output/}"
    install \
      -vDm644 \
      "${_src}" \
      "${_dst}"
  done < <(find \
             "Documentation" \
             -name \
               '.*' \
             -prune \
             -o \
           ! -type \
               "d" \
             -print0)
  echo \
    "Adding symlink..."
  mkdir \
    -p \
    "${pkgdir}/usr/share/doc"
  ln \
    -sr \
    "${builddir}/Documentation" \
    "${pkgdir}/usr/share/doc/${pkgbase}" || \
  true
}

pkgname=(
  "${_pkg}"
  "${_pkg}-headers"
)
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-docs"
  )
fi
for _p in "${pkgname[@]}"; do
  eval \
    "package_${_p}() {
      $(declare \
          -f \
          "_package${_p#$_pkg}")
      _package${_p#$_pkg}
     }"
done

# vim:set ts=8 sts=2 sw=2 et:
