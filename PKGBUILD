#    n SPDX-License-Identifier: AGPL-3.0
            true ) > \
     
#        ----------------------------------------------------------------------
#        Copyright © 2024, 2025, 2026  Pellegrino Prevete
#    
#        All rights reserved
#        ----------------------------------------------------------------------
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


# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
#   David Runge
#     <dvzrv@archlinux.org>
#   Levente Polyak
#     <anthraxx[at]archlinux[dot]org>
#   Lukas Fleischer
#     <lfleischer@archlinux.org>

# Contributors:
#   Gaetan Bisson
#     <bisson@archlinux.org>
#   Tobias Powalowski
#     <tpowa@archlinux.org>
#   Andreas Radke
#     <andyrtr@archlinux.org>
#   Judd Vinet
#     <jvinet@zeroflux.org>

_os="$(
  uname \
    -o)"
if [[ "${_os}" == "Android" ]]; then
  _libc="ndk-sysroot"
  _compiler="clang"
  _libcompiler="llvm-libs"
elif [[ "${_os}" == "GNU/Linux" ]]; then
  _libc="glibc"
  _compiler="gcc"
  _libcompiler="libgcc"
fi
_evmfs_available="$(
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
  _git="true"
fi
if [[ ! -v "_ns" ]]; then
  # _ns="gnupg"
  _ns="freepg"
fi
if [[ ! -v "_archive_format" ]]; then
  if [[ "${_git}" == "true" ]]; then
    if [[ "${_evmfs}" == "true" ]]; then
      _archive_format="bundle"
    elif [[ "${_evmfs}" == "false" ]]; then
      _archive_format="git"
    fi
  elif [[ "${_git}" == "false" ]]; then
    if [[ "${_git_service}" == "github" ]]; then
      _archive_format="zip"
    elif [[ "${_git_service}" == "gitlab" ]]; then
      _archive_format="tar.gz"
    fi
  fi
fi
_pkg=gnupg
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
pkgver=2.5.18
_2_5_18_commit="1b8362889a522bbcfeb80ef3af61218db216f62b"
_2_5_18_freepg_commit="756502e158cc2742a956333997037f72ee5ff40f"
_commit="${_2_5_18_freepg_commit}"
_libassuan_pkgver="3.0.2"
pkgrel=27
_pkgdesc=(
  'Complete and free implementation'
  'of the OpenPGP standard.'
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  "aarch64"
  "arm"
  "i686"
  "mips"
  "x86_64"
)
url="https://www.${_pkg}.org"
license=(
  "BSD-2-Clause"
  "BSD-3-Clause"
  "BSD-4-Clause"
  "CC0-1.0"
  "GPL-2.0-or-later"
  "GPL-3.0-or-later"
  "LGPL-2.1-or-later"
  'LGPL-3.0-or-later OR GPL-2.0-or-later'
  "MIT"
  "Unicode-TOU"
)
depends=(
  "${_libc}"
  "gnutls"
  "libgcrypt"
  "libgpg-error"
  "${_libcompiler}"
  "libksba"
  "libldap"
  "libusb"
  "pinentry"
  "sh"
  "sqlite"
  "tpm2-tss"
  "zlib"
)
makedepends=(
  "bzip2"
  "fig2dev"
  "imagemagick"
  "libassuan>=${_libassuan_pkgver}"
  "librsvg"
  "npth"
  "pcsclite"
  "readline"
  # part of base-devel
  "gettext"
  "${_compiler}"
  "${_libcompiler}"
)
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    "git" 
  )
fi
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs" 
  )
fi
checkdepends=(
  "openssh"
)
_pcslite_optdepends=(
  "pcsclite:"
    "for using scdaemon not with the"
    "gnupg internal card driver."
)
optdepends=(
  "${_pcslite_optdepends[*]}"
)
install="${_pkg}.install"
if [[ "${_ns}" == "gnupg" ]]; then
  _url="https://dev.${_pkg}.org/source/${_pkg}.git"
elif [[ "${_ns}" == "freepg" ]]; then
  _url="https://gitlab.com/${_ns}/${_pkg}"
fi
_tag_name="commit"
if [[ "${_tag_name}" == "commit" ]]; then
  _tag="${_commit}"
elif [[ "${_tag_name}" == "tag" ]]; then
  if [[ "${_ns}" == "gnupg" ]]; then
    _tag="${_pkg}-${pkgver}"
  elif [[ "${_ns}" == "freepg" ]]; then
    _tag="${_pkg}-${pkgver}-freepg"
  fi
fi
_tarname="${_pkg}-${_tag}"
_tarfile="${_pkg}-${_tag}.${_archive_format}"
if [[ "${_git}" == "true" ]]; then
  _src="${_tarfile}::git+${_url}#${_tag_name}=${_tag}"
  if [[ "${_tag_name}" == "tag" ]]; then
    _sum='383fd9720a966825b9d5e45a2b49b3b340ebed356252c73cca242b26dffec0ba'
    _b2_sum='c6b16d797b13e91c4f3eb41d28a69a5854e1744eaac662058cc5332b69b90349a79b891895b7460027bd6234394a4caf36f800d20a74c696a049764112f00658'
  elif [[ "${_tag_name}" == "commit" ]]; then
    _sum="SKIP"
    _b2_sum="SKIP"
  fi
fi
source=(
  "${_src}"
  "dirmngr"{"","@"}"."{"service","socket"}
  "gpg-agent"{"","@"}.{"service","socket"}
  "gpg-agent-"{"browser","extra","ssh"}{"","@"}".socket"
  "keyboxd"{"","@"}.{"service","socket"}
  "keyboxd.8"
  # do not emit beta warnings
  # (due to misbehaving build system)
  # "${_pkg}-2.4-avoid_beta_warning.patch"
  # patches maintained by freepg project:
  # https://gitlab.com/freepg/gnupg/-/commits/gnupg-2.5.18-freepg
  # "0001-gpg-accept-subkeys-with-a-good-revocation-but-no-sel.patch"
  # "0002-gpg-allow-import-of-previously-known-keys-even-witho.patch"
  # "0003-tests-add-test-cases-for-import-without-uid.patch"
  # "0004-gpg-drop-import-clean-from-default-keyserver-import-.patch"
  # "0005-avoid-systemd-deprecation-warning.patch"
  # "0006-Add-systemd-support-for-keyboxd.patch"
  # "0007-Ship-sample-systemd-unit-files.patch"
  # "0008-gpg-default-El-Gamal-to-3072-bit-keys.patch"
  # "0009-gpg-Always-support-and-default-to-using-SHA-512.patch"
  # "0010-gpg-Prefer-SHA-512-and-SHA-384-in-personal-digest-pr.patch"
  # "0012-Disallow-compressed-signatures-and-certificates.patch"
  # "0011-Avoid-simple-memory-dumps-via-ptrace.patch"
  # "0013-ssh-agent-emulation-under-systemd-inject-SSH_AUTH_SO.patch"
  # "0014-gpg-Sync-compliance-mode-cleanup-with-master.patch"
  # "0015-gpg-emit-RSA-pubkey-algorithm-when-in-compatibility-.patch"
  # "0016-gpg-Reintroduce-openpgp-as-distinct-from-rfc4880.patch"
  # "0017-gpg-Emit-LibrePGP-material-only-in-compliance-gnupg.patch"
  # "0018-gpg-gpgconf-list-report-actual-compliance-mode.patch"
  # "0019-gpg-Default-to-compliance-openpgp.patch"
  # "0020-gpg-Fix-newlines-in-Cleartext-Signature-Framework-CS.patch"
  # "0021-Add-keyboxd-systemd-support.patch"
  # "0022-Support-large-RSA-keygen-in-non-batch-mode.patch"
  # "0023-gpg-Verify-Text-mode-Signatures-over-binary-Literal-.patch"
  # "0024-gpg-Do-not-use-a-default-when-asking-for-another-out.patch"
)
sha256sums=(
  "${_sum}"
  '80a3a80f9f1f337da555a6838483e1baca44cde8a8a3d8c4ba7743626304b981'
  '8374255ce93a3c343019ab425963bcbc41982ea89e669d1ad1df0aa7be810de1'
  'ca55048f992824a24ab7f61cbc44a713a153f70a1a60d1cbba7ab4440302a204'
  'd0d79d76bbf6c0d744ee262882fcdfbe52601c6d74cdc5dd99a15da1cdbb6ae1'
  '8ea489a57edb0db9394bf2d6c0ec62205f881bb54efb919e4870209c7db01aa7'
  '81e9dd05cbf3b8406367258eae6ef67ff97f270301bf50b52742647c515c8304'
  'f735119afa3c452728e899809aa1d87b6091a327934befde3aef70ea9259197f'
  '2af0824fdbb95c1c6b54a9ab0a22aeb92ac997e44112f93919d263efa81909ae'
  '1cf9821b3bf4efaf4da2fd52ceb70d254dc4f6c545603f9045de716ef6aabf2d'
  '402eb8f875daaa419f9fdef59ffa84a1e063cc79e04d885ab0768788a4620ac0'
  'f0094f67586cbcda17fd0d780e3e73d6dbaa479ac84715ba941531f83f6ecfe9'
  '6644d769f7919ad58d3caf955195047c521328d180ee2077b78b7f1459f3184b'
  'ffa0191fad52712732f8b24d7d570c1d19a7803e59d30088797b76e252f65858'
  'ddfeafd4b86ef4dd7bcc841115483bcda58c660547ebaeae47ee343741e571eb'
  'cba1aa10c072d982135d2367a7e957d6787037ab232fd148144eca39a92ec2e6'
  '2e3e6ce050737c3bc0e608f283bdfef5471def2ff12dee7ef007854033178694'
  '34144a8e43fbeac88f1ddaf1621e6a3b192efba4580d18a42254ad386819afea'
  '50a00213e44ff07b385e12bca455cd5eec35b271ca2fe500bfe7704ebd8ec73d'
  '38c66efbd3bffdfa9cb0f226a6db03ae4b226f705dc2d0266a555d8ace823b79'
)
b2sums=(
  "${_b2_sum}"
  '7a3af856305eb4b00929aaf029dd4e5c84376df4f30add76976b9b058addf6fc4d8c39335fc83d11493ea9d8a40f0510dbac8572b99a8c8b9b3a4eca8e585774'
  'ee51a4702715f5ec2629ff42eeba8630010da8a67545d1e53961e710de5faf197708e55d2d55796917a134ca2a76b1d6c88a8f7756d0706e0cbc33b605f52d86'
  '3f40de2bf73e84f099b542349257ef6c098b4e347fb218d21a2a785830aa335832229b24c74aadae73deff5460f8645e2d7e7c3c2faaeb91cc812eeb06ddca84'
  '10c6074d67addd5c244a2e83485ed0fd34847e16619e2ff4a5ab09011ed9daf199b7d7b5f109a1ea88a6ba3218e442c6c28575879b305686a13c8a93612937a3'
  'ad71d7fab2a92a8da454c34884b5724e94adc0925a7f97f062fb7b78ed3ec87e5babb6383e755c943afd16bf61789ba83455dc2baf82ce248c1c4622ff87e364'
  '129ecd9df3f00ed28f494f914483645e9aeaa1d6812c762ded60582c0a3f66b215731d4415ea5c017aa5ce97448faa5b93dbcb3793a82643d6ed160cc62f4ea4'
  '36f8709733fbd509f096675a10a240ec6862e6cbd59d32cf8b1fdc1ac04fb7137093690cd97db705e324f6d030344d1d72384504f3465cffccb855c2e29be678'
  '1da101e67ac09eebbb0682d465075a3657c614426c70907d36fd56fee27df082df6536ac47273f41cd7e145e9ab536a3887a9b118cd8b05887a384070294ceca'
  'bf5daa4a33daae716a1d7743470dae618151e14ab7bb5d99138f880a908fac57dbb517b78d92c81ecf4532c25366cd32f7acc0e33a711ccde830fbc208726e69'
  '8a4d1f57c3223c817f840ee989532a57760ad4f836950d18149f4827746f3e7cfb2a1ebdbb115be7c049b5971802eaed9e99125b39cac26b5186b18f9693da99'
  'ffc8ea3c7875b195720ad238742a726b4b7be0bb8f2f8927358d259202f22b5e32f9ad23a4c66da85e25f36544770c29725be6d99256b685427b94d814e29196'
  'c2d29d2adbff690099e537d294d08f9ade73f7a744038382f011b4c9f93c29e27629b740dae02361a4e663730459db6fa81bc2903595fe52e71407dab6590ca2'
  '9dd03f808af45752a01ccbcfec3f3cb39f1a720088e21aa8a19c2ceec3876b3a8b950c1c154203d0adc208fed8ae07a26c8cd59d783e32eb1294a3a340bedad4'
  '91b2a13fdd2c20c5950ec42c742e8be8ee2b6137a9e73e20cf269415fcc960e90049ab3ca6ec8ddc045a8fa03b16396849494b86ebb742adabb53e2703f2d290'
  'cd8578ae69d58d4818b0aecca95fa5080586dfaa9bc5050a7203b0f48e50ad64c5b7c1f71e71711ed120223eb2662e96f577855f729bdf10d2cd648a9e305bfe'
  '4f206967e3d8d1066f5bcb64c35a72bc5f6d69d484b2ab52fd239f4b92b398cdd08c9a016c5dc07fc5cbfdb05983969830983531fae70f67a6a5f61624336577'
  '61e262c714f0e2f9e2a595f16f203c41df93fbfd3aaf20c3ccdbc2bc6c0285a6591b21346f5f15b23f624e1f72470d5d6e1e805979858ea391c815bc1d2e7c67'
  'af13f78ff240c00d9e61bd470ace03bc6926e1cf946016c8c4fa27706ed278babc0ec8a04c79b930d9047f62bd7cfcfeba3e7fd493da7476a318fc49ff0e54fe'
  '5e4fed3c54785fc0140a1cfe970c6ed6a61c0041961999a9777dfcb0050d45e2b9231b3e5e97e025cefe1461614b599bc7129eea931d1996f4849cd83f546abc'
)
validpgpkeys=(
  # Andre Heinecke (Release Signing Key)
  '5B80C5754298F0CB55D8ED6ABCEF7E294B092E28'
  # Werner Koch (dist signing 2020)
  '6DAA6E64A76D2840571B4902528897B826403ADA'
  # Niibe Yutaka (GnuPG Release Key)
  'AC8E115BF73E2D8D47FA9908E98E9B2D19C6C8BD'
  # GnuPG.com (Release Signing Key 2021)
  '02F38DFF731FF97CB039A1DA549E695E905BA208'
)

prepare() {
  local \
    _src
  if [[ "${_archive_format}" == "git" ]]; then
    mv \
      "${srcdir}/${_tarfile}" \
      "${srcdir}/${_tarname}"
  else
    echo \
      "Archive format: '${_archive_format}'"
  fi
  ls \
    "${srcdir}"
  cd \
    "${srcdir}/${_tarname}"
  for _src in "${source[@]}"; do
    _src="${_src%%::*}"
    _src="${_src##*/}"
    [[ "${src}" = *".patch" ]] ||
    continue
    printf \
      "Applying patch %s...\n" \
      "${_src}"
    patch \
      -Np1 < \
      "../${_src}"
  done
  sed \
    -n \
      '5, 28 p' \
    "COPYING.other" > \
    "MIT.txt"
  sed \
    -n \
      '30, 60 p' \
    "COPYING.other" > \
    "BSD-4-Clause.txt"
  sed \
    -n \
      '62, 92 p' \
    "COPYING.other" > \
    "BSD-3-Clause.txt"
  sed \
    -n \
      '95, 125 p' \
    "COPYING.other" > \
    "BSD-2-Clause.txt"
  sed \
    -n \
      '128, 160 p' \
    "COPYING.other" > \
    "Unicode-TOU.txt"
  "./autogen.sh"
}

build() {
  local \
    _configure_opts=()
  _configure_opts=(
    --enable-g13
    --enable-large-secmem  # prerequisite for large RSA keys
    --enable-maintainer-mode
    --libexecdir="/usr/lib/gnupg"
    --prefix="/usr"
    --sbindir="/usr/bin"
    --sysconfdir="/etc"
  )
  cd \
    "${_tarname}"
  "./configure" \
    "${_configure_opts[@]}"
  make
}

check() {
  cd \
    "${_tarname}"
  make \
    check
}

package() {
  local \
    _make_opts=() \
    _systemdir \
    _unit \
    _wantsdir
  _systemdir="${pkgdir}/usr/lib/systemd"
  _wantsdir="${_systemdir}/user/sockets.target.wants"
  _make_opts+=(
    DESTDIR="${pkgdir}"
  )
  depends+=(
    "bzip2"
    "libbz2.so"
    "libassuan>=${_libassuan_pkgver}"
    "libassuan.so"
    "npth"
    "libnpth.so"
    "readline"
    "libreadline.so"
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install
  ln \
    -s \
    "gpg" \
    "${pkgdir}/usr/bin/gpg2"
  ln \
    -s \
    "gpgv" \
    "${pkgdir}/usr/bin/gpgv2"
  install \
    -vDm644 \
    "../keyboxd.8" \
    -t \
    "${pkgdir}/usr/share/man/man8/"
  install \
    -vDm644 \
    {"BSD-"{"2","3","4"}"-Clause","MIT","Unicode-TOU"}.txt \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
  install \
    -vdm755 \
    "${_wantsdir}"
  for _unit in "../"*"."{"service","socket"}; do
    case $_unit in
      *@.*)
        install \
          -vDm644 \
          "${_unit}"
          -t \
          "${_systemdir}/system/" ;;
      *.socket)
        ln \
          -sv \
          "../${_unit##*/}" \
          -t \
          "${_wantsdir}/" ;&
      *)
        install \
          -vDm644 \
          "${_unit}" \
          -t \
          "${_systemdir}/user/" ;;
    esac
  done
}

# vim: ts=2 sw=2 et:
