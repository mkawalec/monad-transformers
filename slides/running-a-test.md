##  Running a test

<pre>
    <code class='haskell'>
    testLoginFailure :: IO ()
    testLoginFailure = do
      conn <- getConn
      let testState = defState
      atomically . writeTVar . bytesToRead $ testState "NO [ALERT] Invalid credentials (Failure)"

      (res, _) <- flip runStateT testState $ do
        login conn "a" "b"

      resultState res @?= NO
    </code>
</pre>
