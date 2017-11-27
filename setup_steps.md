

SEE: https://github.com/google/earthengine-api/issues/27


sudo pip install google-api-python-client 

sudo pip install pyCrypto --upgrade

sudo pip install earthengine-api

earthengine authenticate

  --> returns error:

    pkg_resources.DistributionNotFound: cryptography>=1.9

sudo pip install cryptography

  --> returns error:

    build/temp.macosx-10.6-x86_64-2.7/_openssl.c:483:30: fatal error: openssl/opensslv.h: No such file or directory

     #include <openssl/opensslv.h>

                                  ^

    compilation terminated.

    error: command 'gcc' failed with exit status 1

    ----------------------------------------
    Cleaning up...
    Command /Users/benjaminstocker/Library/Enthought/Canopy_64bit/User/bin/python -c "import setuptools, tokenize;__file__='/Users/benjaminstocker/Library/Enthought/Canopy_64bit/User/build/cryptography/setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --record /tmp/pip-p9YT89-record/install-record.txt --single-version-externally-managed --compile --install-headers /Users/benjaminstocker/Library/Enthought/Canopy_64bit/User/include/site/python2.7 failed with error code 1 in /Users/benjaminstocker/Library/Enthought/Canopy_64bit/User/build/cryptography
    Storing debug log for failure in /Users/benjaminstocker/.pip/pip.log

  Successful installation with:  

  pip install cryptography --global-option=build_ext --global-option="-L/usr/local/opt/openssl/lib" --global-option="-I/usr/local/opt/openssl/include"

  Then again:

  earthengine authenticate

  python -c "import ee; ee.Initialize()"

sudo pip install cffi


Got it to run. Error at statement 'df.sort_values(by = 'date')':

  processing: site at -71.287575 / 44.064665
  Traceback (most recent call last):
    File "gee_subset/gee_subset.py", line 198, in <module>
      pad = args.pad)
    File "gee_subset/gee_subset.py", line 149, in gee_subset
      df.sort_values(by = 'date')
    File "/Users/benjaminstocker/Library/Enthought/Canopy_64bit/User/lib/python2.7/site-packages/pandas/core/generic.py", line 1947, in __getattr__
      (type(self).__name__, name))
  AttributeError: 'DataFrame' object has no attribute 'sort_values'

  --> apparently: "Hello sort_values is new in version 0.17.0, so check your version of pandas. In the previous versions you should use sort." (https://stackoverflow.com/questions/34499728/dataframe-object-has-no-attribute-sort-values)

Therefore I had to update pandas and (as a requirement) numpy.

  sudo pip install numpy --upgrade
  sudo pip install pandas --upgrade

