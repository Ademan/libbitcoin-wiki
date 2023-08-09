With the exception of [cert-new](bx-cert-new), any BX command that requires a random number obtains that value as an argument. This places the responsibility of ensuring random number strength on end-users and also helps them understand the potential for problems.

> The `cert-new` command uses platform random number generation due to its reliance on the underlying [Curve ZMQ](http://curvezmq.org) implementation.

The [seed](bx-seed) command is provided as a convenience for demonstrative purposes only, and **should never be used to secure real bitcoin**.

```
$ bx help seed

Usage: bx seed [-h] [--bit_length value] [--config value]                

Info: Generate a pseudorandom seed.                                      

Options (named):

-b [--bit_length]    The length of the seed in bits. Must be divisible by
                     8 and must not be less than 128, defaults to 192.   
-c [--config]        The path to the configuration settings file.        
-h [--help]          Get a description and instructions for this command.
```

Example usage:

```sh
$ bx seed -b 256
```
```
e4d28a5972ce0785477f39f58e424c5ef643b26894c50f8e024601f87736b8fe 
```
BX utilizes libbitcoin's deterministic ECDSA and as such requires no seed for signing.
