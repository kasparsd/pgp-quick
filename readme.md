# PGP Encrypt/Decrypt Clipboard

A set of bash scripts to simplify the encryption and decryption of any content you have copied to the clipboard (Cmd+C). Automatically searches the [pgp.mit.edu keyserver](https://pgp.mit.edu/) for unknown recipients.

![Screenshot of the terminal output](screenshot.png)

## Requirements

Download and install [GnuPG for OS X](http://sourceforge.net/p/gpgosx/docu/Download/) or using [Homebrew](http://brew.sh/): 

	brew install gpg

## Install

	git clone https://github.com/kasparsd/pgp-quick.git

## Usage

### Encrypt Clipboard

Simply copy the text you want to encrypt and double click the `encrypt-clipboard` file or run it from the terminal:

	./encrypt-clipboard
