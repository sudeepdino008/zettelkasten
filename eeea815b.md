---
date: 2020-10-25T19:35
---

# Haskell workflows

- `ghci` for haskell REPL.

```bash
# change prompt
:set prompt "ghci> "

# enable multi-line input
ghci> :set +m

# load file
:l file.hs
```
In emacs, do `C-c C-l` to load file
Type `main` in prompt to execute the main module

- Loaded files must have main module
```
isp n = floor f == ceiling f  where f = ((1 + sqrt (1 + 24 * n)) / 6)
pentagons = [floor x | x <- [1,2..], isp x]

main = 
  print (take 2 pentagons)
```

## [Haskell/Indentation](https://en.wikibooks.org/wiki/Haskell/Indentation)
**Golden rule**: Code which is part of some expression should be indented further in than the beginning of that expression (even if the expression is not the leftmost element of the line).  
Semicolons and curly braces can be used removing the need to rely on indentation
