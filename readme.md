# pyTorReq

A simple library that allows you to run your requests through the tor network

Basic usage:
```
from pytorreq import PyTorReq

# If you want to use the library on windows, you need to explicitly specify where tor.exe is located.
# Or specify in the system PATH.
torPath = 'tor.exe'
treq = PyTorReq(torPath=torPath)

# If on Linux, then you can not enter anything.
treq = PyTorReq()

response = treq.get('http://ipecho.net/plain')

# Is your new tor ip.
print(response.text)
```

## Installation

```
pip istall pytorreq
```

## Dependencies

You need tor. On windows you can download tor browser, and somewhere inside the tor browser folder you will need to find tor.exe.

Everything is simpler on Linux, I think that linux users do not need to be told what they need to do) like apt\dnf bla bla bla...

## Note

By default, tor session is generated during class initialization. To get a session object, you can directly refer to it.

```
treq = PyTorReq(torPath=torPath)
tses = treq.session
<requests.sessions.Session object at 0x000001FAF5D77B80>
```

The library has two methods of resetting personality, you can use the one you like best.
```
treq.reset_identity()
treq.reset_identity_async()
```
There is a wrapper around all the required request methods.
Just use them as you would with the good old requests module:
```
# GET
treq.get()
# POST
treq.post()
# PUT
treq.put()
# PATCH
treq.patch()
# DELETE
treq.delete()
```

There are also methods for working with cookies.
You can safely transfer regular cookies from requests there.

```
# CookieJar obj
treq.getCookieObj()
# CookiesDict
treq.getCookieDict()
# If you need, you can very simply add a new cookie to the current tor session. Accepts a cookie obj
treq.updateTorSessionCookie(cookie)
```

Close method.
```
# It will close the session.
treq.close()
```