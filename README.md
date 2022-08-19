# haskell-hello-world

testing linux arm64 virtual machine

<br>

## Run With:

`stack build && stack exec haskell-hello-world-exe`

<br>

## Install:

<br>

### Apple Silicon & VMware Fusion

As virtual machine [tech previews](https://blogs.vmware.com/teamfusion/2022/07/just-released-vmware-fusion-22h2-tech-preview.html) become available for Apple Silicon, let's try out some distros as candidate sandboxes:

| distro               | result              |
| :--                  | :--                 |
| <del>Ubuntu 22</del> | <H5 style = "color:red">iso can't be read   |
| <del>Fedora 36</del> | <H5 style = "color:red">incompatible llvm   |
| <del>Fedora 35</del> | <H5 style = "color:red">iso can't be booted |
| Debian 11            | <H3 style = "color:green">success           |

<br>

### Haskell & VS Code

1. While [Haskell](https://www.haskell.org/downloads/) has added instructions for Nix, the recommended installation method is still [GHCup](https://www.haskell.org/ghcup/):
    - Install Haskell, Cabal, and Stack using GHCup (we'll install the Haskell Language server in VS Code at a separate step)
    - Be prepared to do some googling to find the odd package names of missing dependencies, e.g.,: `apt-get install -y build-essential curl libffi-dev libffi7 libgmp-dev libgmp10 libncurses-dev libncurses5 libtinfo5`

<br>

2. Let Stack know about GHCup:

    ```bash
    [ Info  ] Stack manages GHC versions internally by default. In order to make it use ghcup installed
    [ ...   ] GHC versions you can run the following commands:
    [ ...   ]   stack config set install-ghc false --global
    [ ...   ]   stack config set system-ghc  true  --global
    ```
<br>

3. Set up VS Code and the Haskell Langauge Server:
    - Install VS Code via the software manager
    - Install the Haskell extension in VS Code (the HLS and the Haskell Syntax Highlighting Support extension will automatically be installed)

<br>

4. Which Haskell version? Running `stack build && stack exec haskell-hello-world-exe` showed `aarch64-linux-ghc-9.0.2`, so I set GHCup to match: `ghcup rm ghc 8.10.7` && `ghcup install ghc 9.0.2`

<br>

5. Troubleshooting:
    - restart HLS
    - restart VS Code
    - `stack clean --full`
