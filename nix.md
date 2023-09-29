# Nix
Nix is a tool that takes a unique approach to package management and system configuration. Learn how to make reproducible, declarative and reliable systems.

## Nix commands and flakes
From the command options:
```sh
nix help --extra-experimental-features 'nix-command flakes'
```
Set permanently in Nix configuration file:
```sh
mkdir -p ~/.config/nix
echo 'extra-experimental-features = nix-command flakes' >> ~/.config/nix/nix.conf
```

## Nix run