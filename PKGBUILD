# Maintainer: David Runge <dvzrv@archlinux.org>
# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Maintainer: Lukas Fleischer <lfleischer@archlinux.org>
# Contributor: Gaetan Bisson <bisson@archlinux.org>
# Contributor: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Andreas Radke <andyrtr@archlinux.org>
# Contributor: Judd Vinet <jvinet@zeroflux.org>

pkgname=gnupg
pkgver=2.4.7
pkgrel=1
pkgdesc='Complete and free implementation of the OpenPGP standard'
arch=(x86_64)
url='https://www.gnupg.org/'
license=(
  BSD-2-Clause
  BSD-3-Clause
  BSD-4-Clause
  CC0-1.0
  GPL-2.0-or-later
  GPL-3.0-or-later
  LGPL-2.1-or-later
  'LGPL-3.0-or-later OR GPL-2.0-or-later'
  MIT
  Unicode-TOU
)
depends=(
  glibc
  gnutls
  libgcrypt
  libgpg-error
  libksba
  libldap
  libusb
  pinentry
  sh
  sqlite
  tpm2-tss
  zlib
)
makedepends=(
  bzip2
  fig2dev
  git
  imagemagick
  libassuan
  librsvg
  npth
  pcsclite
  readline
)
checkdepends=(openssh)
optdepends=(
  'pcsclite: for using scdaemon not with the gnupg internal card driver'
)
install=$pkgname.install
source=(
  git+https://dev.gnupg.org/source/gnupg.git?signed#tag=${pkgname}-${pkgver}
  dirmngr{,@}.{service,socket}
  gpg-agent{,@}.{service,socket}
  gpg-agent-{browser,extra,ssh}{,@}.socket
  keyboxd{,@}.{service,socket}
  $pkgname-2.4-avoid_beta_warning.patch  # do not emit beta warnings (due to misbehaving build system)
  # patches maintained by freepg project: https://gitlab.com/freepg/gnupg
  0001-gpg-accept-subkeys-with-a-good-revocation-but-no-sel.patch
  0002-gpg-allow-import-of-previously-known-keys-even-witho.patch
  0003-tests-add-test-cases-for-import-without-uid.patch
  0004-gpg-drop-import-clean-from-default-keyserver-import-.patch
  0005-Do-not-use-OCB-mode-even-if-AEAD-OCB-key-preference-.patch
  0006-Revert-the-introduction-of-the-RFC4880bis-draft-into.patch
  0007-avoid-systemd-deprecation-warning.patch
  0008-Add-systemd-support-for-keyboxd.patch
  0009-doc-Remove-profile-and-systemd-example-files.patch
  v3-0001-Disallow-compressed-signatures-and-certificates.patch  # CVE-2022-3219
)
sha256sums=('4e946396a8a3cf8e0b997c5ea87e5732efdc7fee2037d96b0eeb911cd350dab0'
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
            '5494b329584ae5321911b4a28a99e94678e317668269365e288df21839ac47b0'
            '36a3e76bb2d79a57bdf316bd2df5cf965fafe33f9ca345b3c3e0b05e903b0cdf'
            'f25c79a2e135f41b9b84bab416be22cbeb5c32dc92d23a463638d2947ece9703'
            'dc949c2ed9f3439d12ab57fd3b0e4b690e17e6cf46b6ec608def4c44adc6fdea'
            '243c3a79295519b3931f9d846cf2af5caa064a78de812ee336dc786c1567b4d0'
            'faf897297f32791c6433e9c9f82c712970c4b8ae7beba3e04045e6fc71c3d521'
            '8a3de769a2dd42d345ed9736ae442f99a5eaf3b74d7d45c478b3940e74b33d06'
            'b7911ab725e92fa6d35d03c07dde9264d86339c9ffd93c47a04745b2a6043170'
            '6e85911257d5c144b2d9e72ed90255e2d2abe3969b46869729f47afdd8b126cb'
            '4b3d7c8d5251742b1aca62ab7760e7cbfec689fecf387852295636da0caed78a'
            '9ede04c0f35c6e99cee934e46e93a585e3974199c16671775da800d32580e26d'
            '04df2639afa45fa3415de8616c991ff6b75e64455ae105a541b77b31f86c4033'
            '82d5309aec5f379bd7b7a2c79c16121f16975fe21546e81358bf78a0e1b594cc'
            '2e6750ebd5f72973c99c8d81cf2cf934419b15844287e859c599ff14d63d35e1'
            '707f45f1458ea8c762e0b6863ede97fe0e2642ada99a0909edc4359ff415419b')
b2sums=('2c53de51bdde9c7107b6cad253ee552987c43a1f8969e7888fb7017811260b62ad7e06fd470693a8a768bf690b596d514b50795add3a27f3587d5fe439e7518e'
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
        '93382c52bcaf14d7a20b561b5ae6fc587ff46ed5e9fa28df956a5732c8aa685b4966de1db2696bd4e3e99a8c3329a8b3070943c1c06e97aab344af3048c38e75'
        '402c0670357ae811ffb7252d762d3385a6bc542161a828aeb15b932fdc4a8ba181af1a4a4cca639d9adb13a99dac15a006386ad41d94cb566e1a2ba62feff1cc'
        'bb88f65e71537e8fec6bb21487589d4c94e590fc580717ce59bf332b748a62d73a1c8c6f8372efaf0253954b03026c6a924e7a947f4ae293ef0afab9bfcfabad'
        'e5f8da906d225e495e975793e7ba996a038ab5e96e8f3855d33499cdd98da1a68739ae13d0ec4bccc598b12bdeadaf1142b3726f6b5a9de5cbbc989806e99187'
        '168855b598714abb27e01e52e0ed1e1a01ab14ffb2ee09d759308375359cd28c0a9f96c6b9dee0a2cc5713aec8ea831858d59f56a0a126bca3e1401b078fc7ab'
        'd9c78a2c5c57c28d18fad7ca6761e2b593980496bfb0dbd16b9feb85b44f365fe93971cf2051c5aa8e3926d7b9d1a530c899fe221ff891b80d1fbcddce362c2f'
        '6c80c1dec8665fdabba83386d9d188cb03f9b57d14553cc499e8dbeb7d5d57efd12b401114bb8b6335c516a4bf90c1427909fa43f0033296c420081765cf4de8'
        'a5c54e3d8532197f1a2fc83b00d1c1238af15e8c0cf9fa87d081cec8b9a191052bb7571b7b66229842ae7df1574bed523bcfc27af7e09fab1a4a6ee17bf74101'
        'd1df71cc42d867803e9fc94915375a417b10f1931e834b5dffd901362e0e06dbe13c83869a0b76cbeb39ed606b220b2ebb4b027859bb154d7ab89cdc39584ca4'
        'a23a28cc7ecaef6c70e5294e6357fcd59ab3760f482573c985e3d61753a45ee520cd472da87bacdc2ed8d6c67b7f27b1b18e2024c9eb25827c1a987fdcde5dcd'
        '15b368bedb37d9d540b856792de7df67619a79248c2970b7e1cc313aad5a0e50a9a62e3afd9d7d4bc2cc2cdf7bf9573cc525887a9a03e05495fd1e70ef3d7060'
        '76e09f672e126afb7c205ea9b59dff237e7e5e53fc8dc294838a10aba33ebe3359078e0d3c2dfd35c01acae8b6dbfa42df20c086fb60b1bc6bf9ed2f53917804'
        '81fa180793711321bd0628162267ee927289fb6df9eb9f64c4aa0c59a6cdada1a89d9d82a77717f9a0ba6f13d7a98f2f45372d8b21a00fcf6a41e5607eeeb4f5'
        'd9c97811bca5c511b9d1bd5abf8303c81f092b12a457c8511f782edf691483af342e41c0194a6671c8ac7c065059b7abf80493191e4ee1eb73c272718eb6e0cb'
        '345866dc0f2bc24967baea4f5580cca040a82919b342a117e28209ae6e46738a22475c9a4194d5af6f5ab3d410100ca0416f8957f3bdfbcd531a407b60a9e358')
validpgpkeys=(
  '5B80C5754298F0CB55D8ED6ABCEF7E294B092E28' # Andre Heinecke (Release Signing Key)
  '6DAA6E64A76D2840571B4902528897B826403ADA' # Werner Koch (dist signing 2020)
  'AC8E115BF73E2D8D47FA9908E98E9B2D19C6C8BD' # Niibe Yutaka (GnuPG Release Key)
  '02F38DFF731FF97CB039A1DA549E695E905BA208' # GnuPG.com (Release Signing Key 2021)
)

prepare() {
  cd $pkgname

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    [[ $src = *.patch ]] || continue
    msg2 "Applying patch $src..."
    patch -Np1 < "../$src"
  done

  sed -n '5, 28 p' COPYING.other > MIT.txt
  sed -n '30, 60 p' COPYING.other > BSD-4-Clause.txt
  sed -n '62, 92 p' COPYING.other > BSD-3-Clause.txt
  sed -n '95, 125 p' COPYING.other > BSD-2-Clause.txt
  sed -n '128, 160 p' COPYING.other > Unicode-TOU.txt

  ./autogen.sh
}

build() {
  local configure_options=(
    --enable-maintainer-mode
    --libexecdir=/usr/lib/gnupg
    --prefix=/usr
    --sbindir=/usr/bin
    --sysconfdir=/etc
  )

  cd $pkgname
  ./configure "${configure_options[@]}"
  make
}

check() {
  cd $pkgname
  make check
}

package() {
  depends+=(
    bzip2 libbz2.so
    libassuan libassuan.so
    npth libnpth.so
    readline libreadline.so
  )

  cd $pkgname
  make DESTDIR="$pkgdir" install
  ln -s gpg "$pkgdir"/usr/bin/gpg2
  ln -s gpgv "$pkgdir"/usr/bin/gpgv2

  install -vDm 644 {BSD-{2,3,4}-Clause,MIT,Unicode-TOU}.txt -t "$pkgdir/usr/share/licenses/$pkgname/"

  local systemdir="$pkgdir/usr/lib/systemd/"
  local wantsdir="${systemdir}user/sockets.target.wants/"
  install -vdm 755 "$wantsdir"

  local unit
  for unit in ../*.{service,socket}; do
    case $unit in
      *@.*) install -vDm 644 "$unit" -t "${systemdir}system/" ;;
      *.socket) ln -sv "../${unit##*/}" -t "$wantsdir" ;&
      *) install -vDm 644 "$unit" -t "${systemdir}user/" ;;
    esac
  done
}

# vim: ts=2 sw=2 et:
