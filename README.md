# Flathub package for muttum

Here you'll find the Flatpak manifest used to build and publish muttum (aka
org.muttum.muttum) on [Flathub](https://flathub.org/en/apps/org.muttum.muttum).

# How to release

Create a new branch from the `main` one, update references to [latest
muttum release](https://gitlab.adorsaz.ch/muttum/muttum/-/releases).

There's a reference for muttum itself and for the dictionaries provided aside.
Don't forget for each to update the release link and the matching file hash.

If muttum release is compatible with a new GNOME platform release, update the
Flatpak manifest to use this new platform.

Install the flatpak builder with:

```sh
$ flatpak remote-add --if-not-exists --user flathub https://dl.flathub.org/repo/flathub.flatpakrepo
$ flatpak install -y flathub org.flatpak.Builder
```

Build on your computer with:

```sh
$ flatpak run --command=flathub-build org.flatpak.Builder --install org.muttum.muttum.yml
```

Then test the build with:

```sh
$ flatpak run org.muttum.muttum
```

Then apply flatpak automatic checks:
```
$ flatpak run --command=flatpak-builder-lint org.flatpak.Builder manifest org.muttum.muttum.yml
$ flatpak run --command=flatpak-builder-lint org.flatpak.Builder repo repo
```

If everything works well, open a Pull Request on the [muttum's Flathub
repository](https://github.com/flathub/org.muttum.muttum).

Reference for this process is available on the [Flathub
documentation](https://docs.flathub.org/docs/for-app-authors/submission).
