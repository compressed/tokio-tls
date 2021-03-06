# tokio-tls

An implementation of TLS/SSL streams for Tokio built on top of the [`native-tls`
crate]

[![Build Status](https://travis-ci.org/tokio-rs/tokio-tls.svg?branch=master)](https://travis-ci.org/tokio-rs/tokio-tls)
[![Build status](https://ci.appveyor.com/api/projects/status/iiut5d2mts6bt5g1?svg=true)](https://ci.appveyor.com/project/alexcrichton/tokio-tls)

[Documentation](https://tokio-rs.github.io/tokio-tls)
[`native-tls` crate]: https://github.com/sfackler/rust-native-tls

## Usage

First, add this to your `Cargo.toml`:

```toml
[dependencies]
native-tls = "0.1"
tokio-tls = "0.1"
```

Next, add this to your crate:

```rust
extern crate native_tls;
extern crate tokio_tls;

use tokio_tls::{TlsConnectorExt, TlsAcceptorExt};
```

This crate provides two extension traits, `TlsConnectorExt` and
`TlsAcceptorExt`, which augment the functionality provided by the [`native-tls`
crate]. These extension traits provide the ability to connect a stream
asynchronously and accept a socket asynchronously. Configuration of TLS
parameters is still done through the support in the `native-tls` crate.

By default the `native-tls` crate currently uses the "platform appropriate"
backend for a TLS implementation. This means:

* On Windows, [SChannel] is used
* On OSX, [SecureTransport] is used
* Everywhere else, [OpenSSL] is used

[SChannel]: https://msdn.microsoft.com/en-us/library/windows/desktop/aa380123%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396
[SecureTransport]: https://developer.apple.com/reference/security/1654508-secure_transport
[OpenSSL]: https://www.openssl.org/

Typically these selections mean that you don't have to worry about a portability
when using TLS, these libraries are all normally installed by default.

# License

`tokio-tls` is primarily distributed under the terms of both the MIT license
and the Apache License (Version 2.0), with portions covered by various BSD-like
licenses.

See LICENSE-APACHE, and LICENSE-MIT for details.

