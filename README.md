CI_HybridSessions
=================

Allows the use of both Native PHP sessions and the Stock CI Session Library with one interface

---

We at Documentopia usually prefer to use native PHP sessions for a number of reasons, the biggest being that they work out of the box everywhere and with almost every browser.   For a number of years we have been utilizing the CI Native Sessions library by Dariusz Debowczyk with some improvements of our own.

Few other downside I think of the Cookie based method are

    Data is controlled by the user (even if it is encrypted)
    Size of the cookies being past back and forth
    Arbitrary cookie length that might cause strange bugs if you exceed

Now the obvious solution is database based sessions but they have their own problems including setup time and the heavier load they put on a system.

All that being said Native sessions are not without their own problems with the biggest being is the server usually garbage collects them.

A couple projects we are working on needed long life authorization keys....

So we have updated our version of Native Sessions to utilize the stock CI sessions and PHP sessions.   You can configure it what keys to keep as cookies and which to keep as native.   That way if you want one key to be a long running cookie you can (ie login authorization) and the rest of the data is just held as native php sessions and GCed in the normal method.

Added Configuration Items

var $cookie_keys = array();
var $always_cookie = FALSE;

These can either be passed in params or via configuration files (or in the library itself)

cookie_keys sets the keys to be passed along to stock CI session library, and always_cookie tells it to pass along everything for double storage in both native and CI

The hope with this is you get the reliability and simplicity of native sessions with the backup capabilities of cookie (or database sessions) when needed
