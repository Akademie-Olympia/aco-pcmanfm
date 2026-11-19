# PCManFM configuration

View, window and behaviour settings for the graphical file manager.

**[Documentation](https://aco-docs.readthedocs.io/en/latest/pcmanfm/)** ·
[Guide](https://aco-docs.readthedocs.io/en/latest/pcmanfm/guide/) ·
[Design & dependencies](https://aco-docs.readthedocs.io/en/latest/pcmanfm/design/) ·
[Installation and updates](https://aco-arch-dotfiles.readthedocs.io/en/latest/arch-package/)

```bash
curl -fsSL https://raw.githubusercontent.com/Akademie-Olympia/aco-arch-dotfiles/main/install.sh | bash -s -- pcmanfm
```

Package: `aco-arch-dotfiles-pcmanfm`. This standalone repository holds the development sources and the package recipe in
`packaging/arch/PKGBUILD`. The documentation of this component lives in the shared
[aco-docs](https://github.com/Akademie-Olympia/aco-docs) repository (one Read the Docs project for all small components).
Push to `main`; after a successful registry build update with `sudo pacman -Syu`. Details and local builds: [PACKAGING.md](PACKAGING.md).

### Customisation

`~/.config/pcmanfm/default/pcmanfm.conf` controls the user profile. libfm and GTK 3 have separate configuration files. Check changes after restarting PCManFM.

Your own changes in the activated user copy survive synchronisation; new differing defaults appear as `.pacnew`.
See [update and recovery](https://aco-arch-dotfiles.readthedocs.io/en/latest/verification/).

[![Package safety](https://github.com/Akademie-Olympia/aco-pcmanfm/actions/workflows/package.yml/badge.svg)](https://github.com/Akademie-Olympia/aco-pcmanfm/actions/workflows/package.yml)

[MIT licence](LICENSE).
