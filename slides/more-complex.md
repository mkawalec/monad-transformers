##  Something more complex

<pre>
    <code class='haskell'>
    newtype MaybeT m a = MaybeT {runMaybeT :: m (Maybe a)}
    instance (Monad a) => Monad (MaybeT m) where
        return = pure
        (MaybeT ma) >>= f =
            MaybeT $ do
                v <- ma
                case v of
                    Nothing -> return Nothing
                    Just y -> runMaybeT (f y)

    </code>
</pre>
