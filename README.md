Shpider.

Copyright 2011 Andrew Pennebaker (added custom options)

Copyright 2009-2010 Johnny Morrice

Shpider is a web automation library for Haskell. It allows you to quickly write crawlers, and for simple cases (like following links) even without reading the page source.
    
It has useful features such as turning relative links from a page into absolute links, options to authorize transactions only on a given domain, and the option to only download html documents.

It also provides a nice syntax for filling out forms.

EXAMPLE

	#!/usr/bin/env runhaskell

	module ShpiderTest where

	import Network.Shpider hiding (get)
	import Network.Shpider.Curl.Opts

	main = do
	  (result, page) <- runShpiderWithOptions [CurlUserAgent "Windows Mozilla"] $ do
	    download "http://browser.yellosoft.us/text.php"

	  case result of
	    Ok -> putStrLn "Ok"
	    _ -> putStrLn "Error"

	  putStrLn $ source page