---
title: Higher order functions
published: 2000-01-03
---

## Folds
A _fold_ is a higher order function that takes a function and a list.  One example is a function that sums the elements in a list, which could be implement as follows:

```haskell
sum :: [Integer] -> Integer
sum [] = 0
sum (x:xs) = x + sum xs
```

The standard library provides four _fold_ functions, `foldr`, `foldl`, `foldr1`, and `foldl1`.

`foldr` is a right-associative function that folds a list from the right to left.  It is defined as follows:

```haskell
foldr :: (a -> b -> b) -> b -> [a] -> b
foldr f acc [] = acc
foldr f acc (x:xs) = f x (foldr f acc xs)
```

As the fold proceeds, `foldr` will use the given function `f` to combine each elements with the running value called the accumulator.