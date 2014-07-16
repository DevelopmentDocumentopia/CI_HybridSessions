CI_HybridSessions
=================

Allows the use of both Native PHP sessions and the Stock CI Session Library with one interface

---
We at Documentopia usually prefer to use native PHP sessions for a number of reasons, the biggest being that they work out of the box everywhere and with almost every browser.   For a number of years we have been utilizing the CI Native Sessions library by Dariusz Debowczyk with some improvements of our own.

Few of the downsides, I think, of the Cookie based method are:

    Data is controlled by the user (even if it is encrypted)
    Size of the cookies being past back and forth
    Arbitrary cookie length that might cause strange bugs if you exceed

Now the obvious solution is database-based sessions but they have their own problems including setup time and the heavier load they put on a system.

All that being said, Native sessions are not without their own problems with the biggest being that the server usually garbage collects them.

A couple of projects we are working on needed long life authorization keys, so we have updated our version of Native Sessions to utilize the stock CI sessions and PHP sessions.   You can configure it what keys to keep as cookies and which to keep as native.   That way if you want one key to be a long running cookie you can (e.g., login authorization) and the rest of the data is just held as native php sessions and GCed in the normal method.
