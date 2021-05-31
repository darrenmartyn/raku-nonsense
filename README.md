# raku-nonsense
Fucking about with Raku, you can follow along. 

## notes.
On ubuntu, do these first.

```
sudo apt install rakudo
sudo apt install perl6-zef
```

then we install "cro" library for http stuff.

```
zef install --/test cro
```

Wait a while, it fails like this:

```
===> Searching for: cro
===> Updating cpan mirror: https://raw.githubusercontent.com/ugexe/Perl6-ecosystems/master/cpan1.json
===> Updating p6c mirror: https://raw.githubusercontent.com/ugexe/Perl6-ecosystems/master/p6c1.json
===> Updated p6c mirror: https://raw.githubusercontent.com/ugexe/Perl6-ecosystems/master/p6c1.json
===> Updated cpan mirror: https://raw.githubusercontent.com/ugexe/Perl6-ecosystems/master/cpan1.json
===> Searching for missing dependencies: IO::Socket::Async::SSL, JSON::Fast, META6, Shell::Command, File::Find, Terminal::ANSIColor, OO::Monitors, YAMLish, Cro::WebSocket, Docker::File, File::Ignore
===> Searching for missing dependencies: JSON::Class:ver<0.0.15+>, JSON::Name, Cro::HTTP, Base64, Digest::SHA1::Native, Crypt::Random, OpenSSL, MIME::Base64, File::Which
===> Searching for missing dependencies: JSON::Marshal:ver<0.0.20+>, JSON::Unmarshal:ver<0.08+>, IO::Path::ChildSecure, HTTP::HPACK, Cro::Core, Cro::TLS, JSON::JWT, DateTime::Parse, Log::Timeline, if, LibraryMake
===> Searching for missing dependencies: Digest::HMAC
===> Searching for missing dependencies: Digest
===> Building: OpenSSL:ver<0.1.24>:auth<github:sergot>
===> Building [OK] for OpenSSL:ver<0.1.24>:auth<github:sergot>
===> Building: Digest::SHA1::Native:ver<0.04>
[Digest::SHA1::Native] /usr/bin/ld: cannot find -ltommath
[Digest::SHA1::Native] /usr/bin/ld: cannot find -latomic_ops
[Digest::SHA1::Native] /usr/bin/ld: cannot find -luv
[Digest::SHA1::Native] collect2: error: ld returned 1 exit status
[Digest::SHA1::Native] make: *** [Makefile:9: /home/user/.zef/store/p6-digest-sha1-native.git/e34d468341a572a7c089d672429cf88d21e07734/resources/libraries/libsha1.so] Error 1
[Digest::SHA1::Native] The spawned command 'make' exited unsuccessfully (exit code: 2, signal: 0)
[Digest::SHA1::Native]   in method build at /home/user/.zef/store/p6-digest-sha1-native.git/e34d468341a572a7c089d672429cf88d21e07734/Build.pm line 14
[Digest::SHA1::Native]   in block <unit> at -e line 1
===> Building [FAIL]: Digest::SHA1::Native:ver<0.04>
Aborting due to build failure: Digest::SHA1::Native:ver<0.04> (use --force-build to override)
```

Now lets fix that.

```
sudo apt install libuv1-dev libtommath-dev libatomic-ops-dev
```

Now we redo the install of "cro" and this time it fucking works. It takes approximately a billion years to do its thing, feels only slightly less bad than "cpan", probably will fuck your system a bit, but hey - now you have the web thing library.
