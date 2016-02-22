##  Example testable IO function

<pre>
    <code class='haskell'>
    getParsedChunk :: Connection ->
                      (BSC.ByteString -> Result ParseResult) ->
                      IO ParseResult
    getParsedChunk conn parser = do
      (parsed, cont) <- connectionGetChunk'' conn $ parseChunk parser

      if isJust cont
        then getParsedChunk conn $ fromJust cont
        else return . fromJust $ parsed
    </code>
</pre>
