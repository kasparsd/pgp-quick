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

Please take extra care when selecting the key by ensuring the [correct fingerprint](https://en.wikipedia.org/wiki/Public_key_fingerprint). For example, the [about page on kaspars.net](http://kaspars.net/about) lists `A134 BA02 60D4 3F8E ACC8  89D9 94F1 3532 A319 EA5D` as the fingerprint of my public key which indeed matches the one found by the script above.

### Signing and Verification

For example, here is a message that I would like to sign:

	PGP Quick can be found at https://github.com/kasparsd/pgp-quick

so I select and copy that string and run (or click)

	$ ./clearsign-clipboard

which signs the message and stores it into clipboard:

	-----BEGIN PGP SIGNED MESSAGE-----
	Hash: SHA256

	PGP Quick can be found at https://github.com/kasparsd/pgp-quick
	-----BEGIN PGP SIGNATURE-----

	iQEzBAEBCAAdFiEEoTS6AmDUP46syInZlPE1MqMZ6l0FAljFKJQACgkQlPE1MqMZ
	6l0TBAf/SOCCcCzJe1py3oQBErNkdZ+4RaHcsKibIhSlyC0+wSzNCoYA6TPhlqDw
	+ggiYX8zdN0JbLDmKa31HlWB0BPWkzmLfKnXuT+xvfkOTMbdqhM76jsmkgNQ8icG
	/inhMd8BZFaqLqD9aCuJPhxko2ZUMXuyQbSZrBRyT2n+g4iz+Fj+6TrUpjQy+8XA
	ah3z4EXmR1VrQSUf77m85ctZI0rlQMCYo/ci+xqaDQ/tSehAfamJnLoHn9JwzVse
	GUOKFwAZBVCpeIPzqFyJLYJ6ak042PZWF21Q8wGhVWY+AOdJht3bVR15uD2xMcQk
	95WgMzwHfWezpeuHwGxFbXKk11uidw==
	=Xl/W
	-----END PGP SIGNATURE-----

Now everyone can verify that it was written by me:

	$ ./verify-clipboard
	gpg: Signature made Sun Nov 22 01:52:44 2015 EET using RSA key ID 645D5E28
	gpg: Good signature from "Kaspars Dambis <kaspars@damb.is>"

Also https://keybase.io/verify confirms that it was signed by me:

![Verified as signed by Kaspars](http://kaspars.net/wp-content/uploads/2015/11/signed-by-kaspars.png)

## Author

Created by [Kaspars Dambis](http://kaspars.net).

I use these scripts with [Yubikey NEO](https://www.yubico.com/products/yubikey-hardware/yubikey-neo/).
