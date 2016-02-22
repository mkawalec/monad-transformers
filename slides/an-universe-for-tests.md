##  An universe for tests

<pre>
    <code class='haskell'>
    instance {-# OVERLAPPING #-} Universe (S.StateT FakeState IO) where
      connectionPut' = testConnectionPut
      connectionGetChunk'' = testConnectionGetChunk

    data FakeState = FS {
      bytesWritten :: TVar BS.ByteString,
      bytesToRead :: TVar BS.ByteString,
      reactToInput :: (BS.ByteString -> BS.ByteString)
    }
    </code>
</pre>
