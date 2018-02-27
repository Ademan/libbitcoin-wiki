Derive a child HD (BIP32) private key from another HD private key. 
```sh
$ bx hd-private --help
```
```
Usage: bx hd-private [-dh] [--config VALUE] [--index VALUE]              
[HD_PRIVATE_KEY]                                                         

Info: Derive a child HD (BIP32) private key from another HD private key. 

Options (named):

-c [--config]        The path to the configuration settings file.        
-d [--hard]          Signal to create a hardened key.                    
-h [--help]          Get a description and instructions for this command.
-i [--index]         The HD index, defaults to zero.                     

Arguments (positional):

HD_PRIVATE_KEY       The parent HD private key. If not specified the key 
                     is read from STDIN. 
```
### Example 1
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m/0H
```sh
$ bx hd-private -d xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
```
xprv9uHRZZhk6KAJC1avXpDAp4MDc3sQKNxDiPvvkX8Br5ngLNv1TxvUxt4cV1rGL5hj6KCesnDYUhd7oWgT11eZG7XnxHrnYeSvkzY7d2bhkJ7
```
### Example 2
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m/0H/1
```sh
$ bx hd-private -i 1 xprv9uHRZZhk6KAJC1avXpDAp4MDc3sQKNxDiPvvkX8Br5ngLNv1TxvUxt4cV1rGL5hj6KCesnDYUhd7oWgT11eZG7XnxHrnYeSvkzY7d2bhkJ7
```
```
xprv9wTYmMFdV23N2TdNG573QoEsfRrWKQgWeibmLntzniatZvR9BmLnvSxqu53Kw1UmYPxLgboyZQaXwTCg8MSY3H2EU4pWcQDnRnrVA1xe8fs
```
### Example 3
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) chain M/0
```sh
$ bx hd-private xprv9s21ZrQH143K31xYSDQpPDxsXRTUcvj2iNHm5NUtrGiGG5e2DtALGdso3pGz6ssrdK4PFmM8NSpSBHNqPqm55Qn3LqFtT2emdEXVYsCzC2U
```
```
xprv9vHkqa6EV4sPZHYqZznhT2NPtPCjKuDKGY38FBWLvgaDx45zo9WQRUT3dKYnjwih2yJD9mkrocEZXo1ex8G81dwSM1fwqWpWkeS3v86pgKt
```
### Example 4
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) Chain m/0/2147483647H
```sh
$ bx hd-private -d -i 2147483647 xprv9vHkqa6EV4sPZHYqZznhT2NPtPCjKuDKGY38FBWLvgaDx45zo9WQRUT3dKYnjwih2yJD9mkrocEZXo1ex8G81dwSM1fwqWpWkeS3v86pgKt
```
```
xprv9wSp6B7kry3Vj9m1zSnLvN3xH8RdsPP1Mh7fAaR7aRLcQMKTR2vidYEeEg2mUCTAwCd6vnxVrcjfy2kRgVsFawNzmjuHc2YmYRmagcEPdU9
```
### Example 5
piped commands
```sh
$ bx seed | hd-new | hd-private
```
```
875d946b5db47508d67756250f63dd6d
xprv9s21ZrQH143K2odHtyepinTKCiDf8eBUv5fTHtwDHef5VwX79HyVkut91SFpMUvRHF9f2jwkoQ1Z4kpsrpfvS8ZX4QKCcoZoMeXmLWfPKvB
xprv9vHdLyX7nuCbJGV6xHSSi6MxqibjVeiKRF4Z7P2fPKZgpFvmU1oM9mXJqAXCpsHS7FX2Z2fmSTigfeW32bGAQvkLtgQRqgHJPWSptU1gyo6
```

### Example 6
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m/0H/1/2H/2/1000000000
```sh
$ bx hd-new 000102030405060708090a0b0c0d0e0f | bx hd-private -d | bx hd-private -i 1 | bx hd-private -d -i 2 | bx hd-private -i 2 | bx hd-private -i 1000000000
```
```
xprvA41z7zogVVwxVSgdKUHDy1SKmdb533PjDz7J6N6mV6uS3ze1ai8FHa8kmHScGpWmj4WggLyQjgPie1rFSruoUihUZREPSL39UNdE3BBDu76
```