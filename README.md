# WHMCS FreeRADIUS

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/eksoverzero/whmcs-freeradius?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

A FreeRADIUS provisioning/server module for WHMCS

### Installing

##### The files

```
whmcs-freeradius/
  |- whmcs/                  <--- All the files for the WHMCS server
    |- freeradius/           <--- All the files required to create FreeRADIUS accounts
      |- lib/
      |- templates/
      |- tests/
      |  hooks.php
      |  logo.png
      |  freeradius.php
    |- api                   <--- All the files required for FreeRADIUS to speak to WHMCS
      | freeradiusapi.php
  |- freeradius/             <--- All the files for the FreeRADIUS server
    | cron.php
    | config.php.example
  | README.md
```

##### WHMCS

- Copy the `whmcs/freeradius` folder to the `WHMCSROOT/modules/servers/` folder
- Copy the `whmcs/api/freeradiusapi.php` file into the `WHMCSROOT/include/api/` folder

##### FreeRADIUS servers

- Copy the `freeradius` folder to anywhere on the FreeRADIUS server.
- Rename `config.php.example` to `config.php`
- Edit `config.php` with **your** database and WHMCS server details
- Create a Cron task for the `cron.php` file. If you want it to run every 5 minutes:
  
  ```
  */5 * * * * /PATH/TO/php -q /PATH/TO/whmcs-freeradius/freeradius/cron.php
  ```

- On Linux, you can find the `PATH/TO` by running `which php`
