Create a new HD (BIP32) private key from entropy.   
```sh
$ bx hd-new --help
```
```
Usage: bx hd-new [-h] [--config VALUE] [--version VALUE] [SEED]          

Info: Create a new HD (BIP32) private key from entropy.                  

Options (named):

-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
-v [--version]       The desired HD private key version, defaults to     
                     76066276.                                           

Arguments (positional):

SEED                 The Base16 entropy for the new key. Must be at least
                     128 bits in length. If not specified the seed is    
                     read from STDIN.
```
This command supports the `testnet` [configuration setting](Configuration-Settings).
### Example 1
BIP32 [Test Vector 1](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-1) Chain m
```sh
$ bx hd-new 000102030405060708090a0b0c0d0e0f
```
```
xprv9s21ZrQH143K3QTDL4LXw2F7HEK3wJUD2nW2nRk4stbPy6cq3jPPqjiChkVvvNKmPGJxWUtg6LnF5kejMRNNU3TGtRBeJgk33yuGBxrMPHi
```
### Example 2
BIP32 [Test Vector 2](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#test-vector-2) Chain m
```sh
$ bx hd-new fffcf9f6f3f0edeae7e4e1dedbd8d5d2cfccc9c6c3c0bdbab7b4b1aeaba8a5a29f9c999693908d8a8784817e7b7875726f6c696663605d5a5754514e4b484542
```
```
xprv9s21ZrQH143K31xYSDQpPDxsXRTUcvj2iNHm5NUtrGiGG5e2DtALGdso3pGz6ssrdK4PFmM8NSpSBHNqPqm55Qn3LqFtT2emdEXVYsCzC2U
```
### Example 3
short seed error
```sh
$ bx hd-new baadf00dbaadf00d
```
```
The seed is less than 128 bits long.
```
### Example 4
piped commands
```sh
$ bx seed | bx hd-new
```
```
4cd28fdc7efc770749605d59d94fe7b0
xprv9s21ZrQH143K3KDWPNXDFTyieNdyp1ADhcEwqvL7t9CDvvvBaEuwjNVXovz6WXFQPJwWqKe17wNAq3xArJ3qcBZqhVrH2Sq3EQ4en8ig2Fo
```
### Example 5
--version 70615956 (testnet)
```sh
$ bx hd-new -v 70615956 baadf00dbaadf00dbaadf00dbaadf00d
```
```
tprv8ZgxMBicQKsPeQXeTomURYYS8ZhysPog3wXLPwStJ9LeiPeGvypYe4y6HhWadxZi4BB2dLSAMXVkoRi8AoeNXmjETeYFiyRi56BhFnkm9uh
```