How to configure for SubBoard
================

1. Make sure that the I2C interface is enabled and the __/dev/i2c-1__ device is present
2. sudo apt-get install autoconf automake libtool git
3. git clone this repo
4. cd linux_libnfc-nci
5. ./bootstrap
6. ./configure --enable-alt
7. In configuration file "linux_libnfc-nci\conf\libnfc-nxp-init.conf" change the parameter to NXP_NFC_DEV_NODE="/dev/i2c-1"
8. In header "linux_libnfc-nci\src\halimpl\pn54x\tml\i2c\phTmlNfc_alt.h" change GPIO pins in actual: "#define PIN_INT 4" and "#define PIN_ENABLE 5" in "#if (CONFIGURATION == 1)" block
9. make
10. sudo make install
11. export LD_LIBRARY_PATH=/usr/local/lib
12. Check that everything works well by running in tag reader mode "nfcDemoApp poll"


linux_libnfc-nci
================
Linux NFC stack for NCI based NXP NFC Controllers (PN7150, PN7120).

Information about NXP NFC Controller can be found on [NXP website](https://www.nxp.com/products/identification-and-security/nfc/nfc-reader-ics:NFC-READER).

Further details about the stack [here](https://www.nxp.com/doc/AN11697).

Release version
---------------
R2.4 includes dynamic adaptation to the NFC Controller, multiple tags support, and some bug fixes (refer to the [documentation](https://www.nxp.com/doc/AN11697) for more details).

R2.2 includes support for alternative to pn5xx_i2c kernel driver and some bug fixes (refer to the [documentation](https://www.nxp.com/doc/AN11697) for more details).

R2.1 includes support for PN7150 NFC Controller IC and some bug fixes (refer to the [documentation](https://www.nxp.com/doc/AN11697) for more details).

R2.0 includes LLCP1.3 support and some bug fixes (refer to the [documentation](https://www.nxp.com/doc/AN11697) for more details).

R1.0 is the first official release of Linux libnfc-nci stack

Possible problems, known errors and restrictions of R2.4:
---------------------------------------------------------
LLCP1.3 support requires OpenSSL Cryptography and SSL/TLS Toolkit (version 1.0.1j or later)
