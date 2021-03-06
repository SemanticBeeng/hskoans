# Common Functionality for All Monads

All monads as mentioned support these two operations:

Packaging ("return")

```haskell
return :: a -> IO a
return :: a -> [a]
return :: a -> Maybe a
```

Modifying value in the Package ("bind")

```haskell
bind :: IO a -> (a -> IO b) -> IO b
bind :: [a] -> (a -> [b]) -> [b]
bind :: Maybe a (a -> Maybe b) -> Maybe b
```

Other common functions:-

"join" removes the outer package

```haskell
join :: IO (IO a) -> IO a
join :: [[a]] -> [a]
join :: Maybe (Maybe a) -> Maybe a
join mmx = bind mmx id
```

Usage in ghci:

```haskell
> join Nothing
Nothing
```

`join` is a common behavior of any monad.
