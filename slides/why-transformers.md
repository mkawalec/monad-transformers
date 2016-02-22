##  Why transformers

- When we want capabilities of multiple monads
- But we can just do `newtype MaybeIO a = MaybeIO {runMaybe :: IO (Maybe a)}`, right?
- Code reuse, quadratic growth of the number of instances!
