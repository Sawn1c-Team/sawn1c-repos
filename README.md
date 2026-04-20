# Package Upload
> [!IMPORTANT]  
> This is NOT for windows, and I will not be making a windows version, I will support third-party options, but never-the-less, I will not be making this for windows.

> [!CAUTION]
> Use pull requests to add your package here.


Include a package.toml in your folder like this: authorname/packagename. Include your package.toml. your binary tar.xz, and your source tar.xz (both are required, I will consider making the build &/or the binary optional) and include your sha256 verification, and your opengpg key! This below is a toml example, use it for yours:

```
[build]
type         = "autoconf"   # or "cmake", "meson", "custom"
dependencies = ["gcc", "make"]
configure    = "./configure --prefix=/usr/local"
compile      = "make -j{cores}"
install      = "make DESTDIR={stagedir} install"
source_mirror=["source.mirror.link", "diffrent.mirror.link"]

[security]
opengpg      = "(filename of the gpg key you provide on the repos github repo)"
sha256       = "(filename of the sha256 key for binaries/source .tar.xz to prove file is valid)

[binaries]
binary_mirror=["binary.mirror.link", "another.binary.mirror.link"]
```


Compile & configure will run the commands you set it too, I will add toml scanning, do not add malware to my package repos
