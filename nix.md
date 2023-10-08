# Nix

From the official Nix [website](https://nixos.org):
> Nix is a tool that takes a unique approach to package management and system configuration. Learn how to make reproducible, declarative and reliable systems.

## Nix command & flakes

- Provides a modern command-line experience
- Allows for pure reproducibility with Nix flakes
- Highly recommended to enable permanently

*We will assume this feature is always enabled.*

**Enable once as a command-line option:**

```sh
nix --extra-experimental-features 'nix-command flakes' <subcommand>
```

**Enable permanently from the Nix configuration file:**

```sh
mkdir -p ~/.config/nix
echo 'extra-experimental-features = nix-command flakes' >> ~/.config/nix/nix.conf
```

**Enable permanently from the NixOS configuration file:**

```sh
# *.nix
{
  nix.settings.experimental-features = "nix-command flakes";
}
```

## Nix search

- Search for a package and print its description
- Entering invalid package will suggest others with similar names

```sh
nix search nixpkgs#<package>
```

**Example 1:**

```sh
nix search nixpkgs#vim
```

```sh
* legacyPackages.x86_64-linux.vim (9.0.1897)
  The most popular clone of the VI editor
```

**Example 2:**

```sh
nix search nixpkgs#neovi
```

```sh
error: flake 'flake:nixpkgs' does not provide attribute 'packages.x86_64-linux.neovi', 'legacyPackages.x86_64-linux.neovi' or 'neovi'
       Did you mean one of neovim, navi, neo, neo4j or neon?
```

## Nix run


```sh
nix run nixpkgs#<package>
```

**Example:**

```sh
nix run nixpkgs#vim
```

## Nix shell

```sh
nix shell nixpkgs#<package>
```

## Nix profile

```sh
nix profile list
nix profile install <pkg>
nix profile remove <>
nix profile rollback
nix profile upgrade
nix profile history
```