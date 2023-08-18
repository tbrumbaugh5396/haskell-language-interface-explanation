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
- change the permissions of the file to be able to run as an executable
--- sudo chmod 777 Example.hs
- run the file as an executable
--- ./Example.hs

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

## Libraries
Scotty is a web framework to listen to HTTP requests.
Beam is a library to run SQLite queries.

# Interest in running web-servers
When running programs in nixos they must be stopped via: ctrl + z 
Therefore, inorder to kill them we must find the process that is running at the port via: sudo netstat -ltnp
Then, kill that process via: kill -9 [process_id]

