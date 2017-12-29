# NAME

URI::FromHash - Build a URI from a set of named parameters

# VERSION

version 0.05

# SYNOPSIS

    use URI::FromHash qw( uri );

    my $uri = uri(
        path  => '/some/path',
        query => { foo => 1, bar => 2 },
    );

# DESCRIPTION

This module provides a simple one-subroutine "named parameters" style
interface for creating URIs. Underneath the hood it uses `URI.pm`,
though because of the simplified interface it may not support all
possible options for all types of URIs.

It was created for the common case where you just want a simple interface for
creating syntactically correct URIs from known components (like a path and
query string). Doing this using the native `URI.pm` interface is rather
tedious, requiring a number of method calls, which is particularly ugly when
done inside a templating system such as Mason or TT2.

# FUNCTIONS

This module provides two functions both of which are _optionally_
exportable:

## uri( ... ) and uri\_object( ... )

Both of these functions accept the same set of parameters, except for
one additional parameter allowed when calling `uri()`.

The `uri()` function simply returns a string representing a
canonicalized URI based on the provided parameters. The
`uri_object()` function returns new a `URI.pm` object based on the
given parameters.

These parameters are:

- scheme

    The URI's scheme. This is optional, and if none is given you will
    create a schemeless URI. This is useful if you want to create a URI to
    a path on the same server (as is commonly done in `<a>` tags).

- host
- port
- path

    The path can be either a string or an array reference.

    If an array reference is passed each _defined_ member of the array
    will be joined by a single forward slash (/).

    If you are building a host-less URI and want to include a leading
    slash then make the first element of the array reference an empty
    string (`q{}`).

    You can add a trailing slash by making the last element of the array
    reference an empty string.

- username
- password
- fragment

    All of these are optional strings which can be used to specify that
    part of the URI.

- query

    This should be a hash reference of query parameters. The values for
    each key may be a scalar or array reference. Use an array reference to
    provide multiple values for one key.

- query\_separator

    This option is can _only_ be provided when calling `uri()`. By
    default, it is a semi-colon (;).

# BUGS

Please report any bugs or feature requests to
`bug-uri-fromhash@rt.cpan.org`, or through the web interface at
[http://rt.cpan.org](http://rt.cpan.org).  I will be notified, and then you'll automatically be
notified of progress on your bug as I make changes.

Bugs may be submitted at [http://rt.cpan.org/Public/Dist/Display.html?Name=URI-FromHash](http://rt.cpan.org/Public/Dist/Display.html?Name=URI-FromHash) or via email to [bug-uri-fromhash@rt.cpan.org](mailto:bug-uri-fromhash@rt.cpan.org).

I am also usually active on IRC as 'autarch' on `irc://irc.perl.org`.

# SOURCE

The source code repository for URI-FromHash can be found at [https://github.com/houseabsolute/URI-FromHash](https://github.com/houseabsolute/URI-FromHash).

# DONATIONS

If you'd like to thank me for the work I've done on this module, please
consider making a "donation" to me via PayPal. I spend a lot of free time
creating free software, and would appreciate any support you'd care to offer.

Please note that **I am not suggesting that you must do this** in order for me
to continue working on this particular software. I will continue to do so,
inasmuch as I have in the past, for as long as it interests me.

Similarly, a donation made in this way will probably not make me work on this
software much more, unless I get so many donations that I can consider working
on free software full time (let's all have a chuckle at that together).

To donate, log into PayPal and send money to autarch@urth.org, or use the
button at [http://www.urth.org/~autarch/fs-donation.html](http://www.urth.org/~autarch/fs-donation.html).

# AUTHOR

Dave Rolsky <autarch@urth.org>

# COPYRIGHT AND LICENSE

This software is Copyright (c) 2017 by Dave Rolsky.

This is free software, licensed under:

    The Artistic License 2.0 (GPL Compatible)

The full text of the license can be found in the
`LICENSE` file included with this distribution.
