##  The simplest transformer

    newtype IdentityT f a = IdentityT {runIdentityT :: f a}

which is, without record syntax:

    newtype IdentityT f a = IdentityT (f a)
