![](https://github.com/TinoGuo/r_crypto/workflows/CI%20check/badge.svg?branch=master)
[![pub package](https://img.shields.io/pub/v/r_crypto.svg)](https://pub.dartlang.org/packages/r_crypto)
![GitHub](https://img.shields.io/github/license/TinoGuo/r_crypto)
![GitHub top language](https://img.shields.io/github/languages/top/TinoGuo/r_crypto)
![GitHub language count](https://img.shields.io/github/languages/count/TinoGuo/r_crypto.svg)

# desc

Forked from https://github.com/TinoGuo/r_crypto, upgraded the Gradle (8.3) and Kotlin (2.0.0) versions.

Copied the pre-generated libcrypto.so from the r_crypto project on pub.dev to the corresponding directory under android/src/main/jniLibs.

# r_crypto

Rust backend support crypto flutter library, much faster than Dart-implementation library, light-weight library.

Some crypto support hardware accelerate.

## Support Algorithm

### Hashes

- MD5
- SHA1
- SHA2
    - SHA224
    - SHA256
    - SHA384
    - SHA512-trunc224
    - SHA512-trunc256
- SHA3
    - SHA3-224
    - SHA3-256
    - SHA3-384
    - SHA3-512
    - SHAKE-128
    - SHAKE-256
    - KECCAK224
    - KECCAK256
    - KECCAK384
    - KECCAK512
- Whirlpool
- Blake2
    - Blake2b
    - Blake2s
- Blake3
- Groestl
    - Groestl224
    - Groestl256
    - Groestl384
    - Groestl512
    - GroestlBig
    - GroestlSmall
- RIPEMD160 (RIPEMD-320 provides only the same security as RIPEMD-160)
- Shabal
    - Shabal192
    - Shabal224
    - Shabal256
    - Shabal384
    - Shabal512

More digest will support soon.

## Support Platform

- Android
    - arm64-v8a
    - armeabi-v7a
    - x86
    - x86_64
- iOS
    - arm64
    - x86_64
- macOS
    - x86_64
    - arm64(WIP)
- Windows
    - x86_64
    - x86(Not support now and feature)
- Linux
    - x86_64

## Example Usage

### Hash

```dart
import 'package:r_crypto/r_crypto.dart';

// For fixed output length digest
rHash.hashString(HashType.MD5, input);
// For dynamic output length digest
rHash.hashString(HashType.blake3(length: 64), input);
// Also accept List<int> as parameter
rHash.hashList(HashType.KECCAK_224, [0,1,2]);
// Hash File
rHash.filePath(HashType.blake3(length: 32), path);

// Encode the list
hex.encode(list);
```

## Note

- Windows user needs to download the [rcrypto.dll](https://github.com/TinoGuo/r_crypto/releases) and put it in the same folder with *.exe. It's the limitation of the Flutter Windows Plugin now.

## TODO
- [x] Support file input
- [ ] Support encrypt/decrypt algorithm