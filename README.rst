Safari SOP Paste: a client side encrypted pastebin
===========================================

Safari SOP Paste is a pastebin that encrypts the user content in the browser and can run without a database.
Forked from https://github.com/Tygs/0bin

It's an Python implementation of the `zerobin project`_, created by sebsauvage, under the `MIT licence`_.

To run zerobin, download zerobin.pyz from the latest release_ then:

::

    python zerobin.pyz

Safari SOP Paste requires Python 3.7 or higher.

You may need to type :code:`py -3.7 zerobin.pyz` on Windows, or :code:`python3.7 zerobin.pyz` on Mac/Linux, depending on your configuration.

If you are familiar with the Python ecosystem, you can also :code:`python -m pip install zerobin --user` and run :code:`python -m zerobin` for the same effect.


How it works
=============

When creating the paste:

- the browser generates a random key;
- the pasted content is encrypted with this key using AES256;
- the encrypted pasted content is sent to the server;
- the browser receives the paste URL and adds the key in the URL hash (#).

When reading the paste:

- the browser makes the GET request to the paste URL;
- because the key is in the hash, the key is not part of the request;
- browser gets the encrypted content end decrypts it using the key;
- the pasted decrypted content is displayed and sourcecode is highlighted.

Key points:

- because the key is in the hash, the key is never sent to the server;
- therefore it won't appear in the server logs;
- all operations, including code coloration, happen on the client-side;
- the server is no more than a fancy recipient for the encrypted data.

Other features
======================

- automatic code coloration (no need to specify the language);
- pastebin expiration: 1 day, 1 month or never;
- burn after reading: the paste is destroyed after the first reading;
- clone paste: you can't edit a paste, but you can duplicate any of them;
- code upload: if a file is too big, you can upload it instead of using copy/paste;
- copy paste to clipboard in a click;
- own previous pastes history;
- reader mode;

Known issues
============

- 0bin uses several HTML5/CSS3 features that are not widely supported. In that case we handle the degradation as gracefully as we can.
- The pasted content size limit check is not accurate. It's just a safety net, so we think it's ok.


.. _moderate the pastebin content: http://www.zdnet.com/blog/security/pastebin-to-hunt-for-hacker-pastes-anonymous-cries-censorship/11336
.. _zerobin project: https://github.com/sebsauvage/ZeroBin/
.. _node.js: http://nodejs.org/
.. _is not worth it: http://stackoverflow.com/questions/201705/how-many-random-elements-before-md5-produces-collisions
.. _WTFPL licence: https://en.wikipedia.org/wiki/MIT_License
.. _release: https://github.com/SafariSop/0bin/releases

Contributing
=============

Feel free to contribute to the project.
