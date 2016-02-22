##  Instances

<pre>
    <code class='haskell'>
    newtype IdentityT m a = IdentityT {runIdentityT :: m a}

    instance (Functor m) => Functor (IdentityT m) where
        fmap f (IdentityT fa) = IdentityT (fmap f fa)

    instance (Applicative m) => Applicative (IdentityT m) where
        pure x = IdentityT (pure x)
        (IdentityT fab) <*> (IdentityT fa) = IdentityT (fab <*> fa)

    instance (Monad m) => Monad (IdentityT m) where
        return = pure
        (>>=) :: IdentityT m a ->
                (a -> IdentityT m b) ->
                IdentityT m b
        (IdentityT ma) >>= f =
            IdentityT $ ma >>= runIdentityT . f
    </code>
</pre>
