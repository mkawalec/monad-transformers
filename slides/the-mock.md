##  The mock

<pre>
    <code class='haskell'>
    testConnectionGetChunk :: Connection -> (BS.ByteString -> (a, BS.ByteString)) -> S.StateT FakeState IO a
    testConnectionGetChunk c proc = do
      st <- S.get
      toRead <- liftIO . atomically $ do
        bytes <- readTVar . bytesToRead $ st
        if (BS.length bytes) == 0 then retry else return bytes

      let (result, left) = proc toRead
      liftIO . atomically $ writeTVar (bytesToRead st) left
      return result
   </code>
</pre>
