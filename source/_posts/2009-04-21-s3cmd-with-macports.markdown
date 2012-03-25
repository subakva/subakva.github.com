---
date: '2009-04-21 11:52:18'
layout: post
slug: s3cmd-with-macports
status: publish
title: s3cmd with MacPorts
wordpress_id: '98548849'
categories:
- regular
---

I ran into a string of errors while trying to run s3cmd with MacPorts python.




`/opt/local/bin/s3cmd` uses `ParameterError` before importing it. I moved the imports out of the try/except block to get this working:



    
    if __name__ == '__main__':
    
    	from S3 import PkgInfo
    	from S3.S3 import *
    	from S3.Config import Config
    	from S3.S3Uri import *
    	from S3 import Utils
    	from S3.Exceptions import *
    	from S3.Utils import unicodise
    	from S3.Progress import Progress
    	from S3.CloudFront import Cmd as CfCmd
    
    	try:
    
    		main()
    		sys.exit(0)
    
    	except ParameterError, e:
    		error(u"Parameter problem: %s" % e)
    		sys.exit(1)
    




Next, the command died while trying to import _md5. The Python 2.5 port does not include hashlib, which defines _md5. You can install it yourself like so:  
`sudo port install py25-hashlib`




Lastly, while running `s3cmd --configure` and testing my connection with the HTTPS option, I got this warning:  
`WARNING: Retrying failed request: /?delimiter=/ ('module' object has no attribute 'ssl')`




This feature depends on another port, which can be installed with:  
`sudo port install py25-socket-ssl`
