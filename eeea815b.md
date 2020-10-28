---
date: 2020-10-25T19:35
---

# Haskell workflows

- `ghci` for haskell REPL.
- change prompt
```bash
:set prompt "ghci> "
```
- enable multi-line input
```bash
ghci> :set +m
```

- Loaded files must have main module
```
isp n = floor f == ceiling f  where f = ((1 + sqrt (1 + 24 * n)) / 6)
pentagons = [floor x | x <- [1,2..], isp x]

main = 
  print (take 2 pentagons)
```

- load file:
```
:l file.hs
```

In emacs, do `C-c C-l` to load file
Type `main` in prompt to execute the main module
