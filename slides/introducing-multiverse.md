##  Introducing multiverse


<pre>
    <code class='haskell'>
    class Monad m => Universe m where
      connectionPut' :: Connection -> BSC.ByteString -> m ()
      connectionGetChunk'' :: Connection ->
        (BSC.ByteString -> (a, BSC.ByteString)) -> m a

    instance Universe IO where
      connectionPut' = connectionPut
      connectionGetChunk'' = connectionGetChunk'
    </code>
</pre>
