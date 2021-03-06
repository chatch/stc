# Stellar transaction compiler

stc is a command-line tool that translates
[Stellar](https://www.stellar.org/) blockchain transactions back and
forth between human-readable
[txrep](https://github.com/stellar/stellar-protocol/blob/master/ecosystem/sep-0011.md)
format and Stellar's native binary XDR representation.  With stc, you
can create, view, edit, sign, and submit Stellar transactions.

# Installing `stc` for non-developers

To install or upgrade this software if you don't plan to hack on it,
run the following two commands (assuming your GOPATH is in the default
location of `~/go`):

    rm -rf ~/go/src/github.com/xdrpp/stc/
    go get github.com/xdrpp/stc/

The `rm` command is necessary when upgrading because [some `go get`
limitation](https://github.com/golang/go/issues/27526) leaves your
tree in a detached state, so that `go get -u` cannot pull from the
remote `go1` branch.

Once this completes, put the `~/go/bin` directory on your path and you
should be able to run `stc`.

If you'd like to install the `goxdr` XDR compiler, you can also run:

    go get github.com/xdrpp/stc/goxdr

# Using `stc`

See the [man page](stc.1.md)

# Building `stc` for developers

Because `stc` requires autogenerated files, the `master` branch is not
meant to be compiled under `$GOPATH`, but rather in a standalone
directory with a `make`.

Furthermore, to build `stc` you also need to install `goyacc` and the
Go extra `crypto` library.  If you don't already have these installed,
or if your versions are too old, run the following command:

    make update-depend

to install the build-type dependencies under your `$GOPATH` (`~/go` by
default).  Once these dependencies are place, just run:

    make

to build the tool.  If that doesn't work, you may have an old version
of the extra `crypto` library, so make sure to run `make
update-depend`.

To install `stc` you will also need [pandoc](https://pandoc.org/) to
format the man page.

To understand the included `goxdr` XDR compiler, see its [man
page](goxdr/goxdr.1.md).

# Disclaimer

There is no warranty for the program, to the extent permitted by
applicable law.  Except when otherwise stated in writing the copyright
holders and/or other parties provide the program "as is" without
warranty of any kind, either expressed or implied, including, but not
limited to, the implied warranties of merchantability and fitness for
a particular purpose.  The entire risk as to the quality and
performance of the program is with you.  Should the program prove
defective, you assume the cost of all necessary servicing, repair or
correction.

In no event unless required by applicable law or agreed to in writing
will any copyright holder, or any other party who modifies and/or
conveys the program as permitted above, be liable to you for damages,
including any general, special, incidental or consequential damages
arising out of the use or inability to use the program (including but
not limited to loss of data or data being rendered inaccurate or
losses sustained by you or third parties or a failure of the program
to operate with any other programs), even if such holder or other
party has been advised of the possibility of such damages.
