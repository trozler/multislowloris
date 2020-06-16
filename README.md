# multislowloris.py - A multiprocess simple slowloris in Python

This implementation extends the simple slowloris python implmentation given by Gokberk Yaltirakli ([@gkbrk]), by implmenting a multiprocess slowloris DoS attack.

This code was written for purpose of stress testing web servers only.

---

## What is Slowloris?

Slowloris is basically an HTTP Denial of Service attack that affects threaded servers. It works like this:

1. We start making lots of HTTP requests.
2. We send headers periodically (every ~15 seconds) to keep the connections open.
3. We never close the connection unless the server does so. If the server closes a connection, we create a new one keep doing the same thing.

This exhausts the servers thread pool and the server can't reply to other people.

## How to install and run?

- `git clone https://github.com/trozler/multislowloris`
- `cd multislowloris`
- `python3 multislowloris.py example.com`

### SOCKS5 proxy support

However, if you plan on using the `-x` option in order to use a SOCKS5 proxy for connecting instead of a direct connection over your IP address, you will need to install the `PySocks` library (or any other implementation of the `socks` library) as well. [`PySocks`](https://github.com/Anorov/PySocks) is a fork from [`SocksiPy`](http://socksipy.sourceforge.net/) by GitHub user [@Anorov] and can easily be installed by adding `PySocks` to the `pip` command above or running it again like so:

- `sudo pip3 install PySocks`

You can then use the `-x` option to activate SOCKS5 support and the `--proxy-host` and `--proxy-port` option to specify the SOCKS5 proxy host and its port, if they are different from the standard `127.0.0.1:8080`.

## Configuration options

It is possible to modify the behaviour of slowloris with command-line arguments.

## License

The code is licensed under the MIT License.

[@gkbrk]: https://github.com/gkbrk
[@anorov]: https://github.com/Anorov/PySocks
