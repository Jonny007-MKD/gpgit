See https://grepular.com/Automatically_Encrypting_all_Incoming_Email

Usage
=====

This application takes one argument on the command line. The email address to
look up the public key that the message will be encrypted with. An email
message is piped through the application, and the resulting email is sent to
STDOUT encrypted with the relevant public key. If you provide multiple email
addresses, then the message will be encrypted with multiple keys. There are
several options to do with the type of encryption used, ie PGP/MIME or inline
and these can be discovered by running the script without any arguments to
read the usage information.

If the message is already encrypted, it doesn't get encrypted a second time.

Exim users can use the transport_filter directive in a transport in order to
call this application, like so:

  transport_filter = /bin/gpgit.pl my.email.address@example.com

Procmail users can add a procmail recipe as follows

  :0 f
  | /bin/gpgit.pl my.email.address@example.com

If you call gpgit.pl from a different application, I'd love to hear from you so
I can update this README file.

Installation
============

* Install build tools like gcc and make and gpgv:

		apt-get install gcc make gpgv
  
* Get perl dependencies with cpan:
  
		cpan -u   # Upgrade all modules
		cpan install GnuPG::Interface
		cpan install Mail::GnuPG
		cpan install MIME::Tools
		rm -rf $HOME/.cpan/build/ $HOME/.cpan/sources/authors/id/

* Clone this repository: `git clone ...`
  
