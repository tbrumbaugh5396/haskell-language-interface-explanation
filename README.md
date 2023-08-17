# haskell-language-interface-explanation
The purpose of this project is to understand the haskell programming language, especially in respect to NixOS.
This project will also serve as a personal reference.

## This project is in progress.


# Example.hs

Here I will demonstrate how to run a haskell program as a script in the NixOS.

The order to include in the script:
- specify nix-shell
- specify the haskell packages to include
- specify the program to run the script (run ghc) 

```
#! /usr/bin/env nix-shell
#! nix-shell -p "haskellPackages.ghcWithPackages (pkgs: [pkgs.brick])"
#! nix-shell -i runghc

module Main where

import Brick

ui :: Widget ()
ui = str "Hello, world!"

main :: IO ()
main = simpleMain ui
```
