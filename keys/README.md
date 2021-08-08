Signing keys for unofficial OpenJDK LTS builds for Linux/sparc64
---

These are the signing keys for my OpenJDK builds. They're generated
using `signify`, you should be able to verify the integrity
on at least, Linux and OpenBSD systems.

## How to verify

Download the key, tarballs, and `SHA256.sig` files for the release you want
into a single directory, then simply run `signify -C -p jdkXX.pub -x SHA256.sig`.

More information about signify is available in [its manual page](https://man.openbsd.org/signify.1).

## More about the keys

In general, I'm using the following scheme to manage the keys:

- Each major JDK version gets its own key.
- The key for version X will be signed with the key for version X-1.
  (With the exception of JDK 11, since it's the first build I made)
- Generally I'll try to post the keys in multiple places, to help with
  distribution.

(This is inspired by [OpenBSD's approach to signing](https://www.openbsd.org/papers/bsdcan-signify.html))
