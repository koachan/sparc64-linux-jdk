Unofficial OpenJDK LTS builds for Linux/sparc64
---

This is an unofficial OpenJDK LTS builds for Linux/sparc64, mostly provided as
a bootstrap aid so that people can build their own flavor of OpenJDK.

Currently, this is simply a snapshot of the JDK build that I personally use,
which itself initially bootstrapped out of a Debian/sparc64 chroot on a Gentoo
host.

## Where to get it

Look at the [Releases](https://github.com/koachan/sparc64-linux-jdk/releases) page.

## How to use it

1. Download the main OpenJDK tarball, verify the hash and extract it somewhere.
2. [Download the OpenJDK source](https://openjdk.java.net/groups/build/doc/building.html#getting-the-source-code).
3. Apply the patches from the patches/ directory to the source repo, if needed.
4. When running the `configure` script, set the boot JDK option to the place
   where you extracted the binaries.
   (Also, feel free to see the set of flags that I used in the flags/ directory)
5. Proceed to build and install OpenJDK as usual.

Further guidance to building OpenJDK can be read [here](https://openjdk.java.net/groups/build/doc/building.html).

## FAQ

### Will you provide $VERSION builds?

In general, if it's a supported LTS release, I'll try to publish builds.
Otherwise, I won't. Also, if a version goes EOL, I'll try to give one last build
based on its latest release, but after that I'll stop providing updates/rebuilds
to it altogether.

### What about OpenJDK 8? It is still supported, no?

Unfortunately, it's very unlikely that I'd ever provide builds for version 8.
Currently, I personally don't use OpenJDK 8, so there's little interest from
my side to do it. I _might_ do one if I have the time to do it, but overall
it's a lower-priority thing to do for me.

### Why/how is this bootstrapped?

This was originally a JDK from Debian chroot running on a Gentoo base.
Since I want to get rid of the chroot, I tried to make builds that run natively
on Gentoo, those are what I'm sharing here :)

## A note about OpenJDK 17 (and possibly, newer)

OpenJDK [removed](https://openjdk.java.net/jeps/381) SPARC-specific code back
in version 15. Thankfully, it can still be built using the interpreter-only "Zero"
configuration, but since the JIT compiler and SPARC-specific optimizations are gone,
it obviously has lower performance than earlier versions :(

Still, it's better than nothing :)

## TODO

- Create a more standardized build infrastructure.
- Find a better way to host it :)
- Make a Gentoo overlay so that on that distro, it can recognize this build as
  `dev-java/openjdk-bin`.

## Disclaimer & Warning

I think this is very important so I'd reiterate it: _Please do not use these
builds to directly run any Serious Workloads. Instead, use it as a bootstrap
JDK to make your own builds_. As for why, there are two reasons:

- I cannot afford to run a frequent build/publish pipeline, so it is possible
  that the published builds might end up getting severely outdated wrt
  upstream releases
  (and hence, misses important critical and security fixes).
- Also, since these builds are made on a best-effort basis (i.e "works on my
  machine"), chances are using them as-is for real workloads on your machine
  will expose some sort of subtle, hard-to-debug incompatibility problems.

Or, in legalese:

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY
AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT,
INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM
LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR
OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR
PERFORMANCE OF THIS SOFTWARE.

## License

OpenJDK is licensed under [GPLv2 with Classpath Exception](https://openjdk.java.net/legal/gplv2+ce.html).
