# escp2-client
Create ESC-P2 commands for Epson Printers

See paper describing the method at DOI: [10.1039/C8RA00756J](https://pubs.rsc.org/en/content/articlelanding/2018/ra/c8ra00756j#!divAbstract)


## getting printer running from fresh Raspbian Buster Lite

1.  Install fresh Raspbian Buster with Desktop
2.  Get an Epson XP-440 printer
3.  Install CUPS, gutenprint, and epson drivers
    ```shell
    sudo apt-get install cups printer-driver-gutenprint printer-driver-escpr
    ```
4.  Open a browser and enter `localhost:631` to the address bar.
5.  Click "Add Printer" under the Administration menu.
6.  Log in with linux user credentials.  Printer should show up in "local printers" list.  Follow instructions.
