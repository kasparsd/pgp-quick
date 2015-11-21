# PGP Encrypt, Decrypt, Sign and Verify Clipboard

A set of bash scripts to simplify the encryption, decryption, signing and verification of any content you have copied to the clipboard. Automatically searches the [pgp.mit.edu keyserver](https://pgp.mit.edu/) for unknown recipients during encryption.

![Screenshot of the terminal output](screenshot.png)

## Requirements

Download and install [GnuPG for OS X](http://sourceforge.net/p/gpgosx/docu/Download/) or using [Homebrew](http://brew.sh/): 

	$ brew install gpg

## Install

	$ git clone https://github.com/kasparsd/pgp-quick.git

## Usage

### Encryption

Simply copy the text you want to encrypt and double click the `encrypt-clipboard` file or run it from the terminal:

	$ ./encrypt-clipboard

and it will prompt you to enter the recipient email address:

	$ ./encrypt-clipboard
	Enter recipient email address:
	hi@kaspars.net

In case the public key of the recipient is not found in your local keyring, it will search the [pgp.mit.edu](https://pgp.mit.edu/) keyserver and offer you to select from the keys found:

	gpg: D31A263C: There is no assurance this key belongs to the named user

	pub  2048R/D31A263C 2015-11-12 Kaspars Dambis <hi@kaspars.net>
	 Primary key fingerprint: DE94 A9B4 8BE3 6B82 F438  EE72 3352 BC04 645D 5E28
	      Subkey fingerprint: 8C82 56D3 6165 7DF7 A18E  2DCF E3D9 7C52 D31A 263C

	It is NOT certain that the key belongs to the person named
	in the user ID.  If you *really* know what you are doing,
	you may answer the next question with yes.

	Use this key anyway? (y/N)

Please take extra care when selecting the key by ensuring the [correct fingerprint](https://en.wikipedia.org/wiki/Public_key_fingerprint). For example, the [about page on kaspars.net](http://kaspars.net/about) lists `DE94 A9B4 8BE3 6B82 F438  EE72 3352 BC04 645D 5E28` as the fingerprint of my public key which indeed matches the one found by the script above.
