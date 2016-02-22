##  The complexestest

<pre>
    <code class='haskell'>
    newtype StateT s m a = StateT {runStateT :: s -> m (a, s)}
    instance (Monad m) => Monad (StateT s m) where
        return a = StateT $ \s -> return (a,s)

        (>>=) :: StateT s m a ->
                 (a -> StateT s m b) ->
                 StateT s m b
        (StateT x) >>= f = StateT $ \s -> do
            (v,s') <- x s
            runStateT (f v) s'

    </code>
</pre>
