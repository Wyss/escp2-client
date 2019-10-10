# escp2-client
Create ESC-P2 commands for Epson Printers

See paper describing the method at DOI: [10.1039/C8RA00756J](https://pubs.rsc.org/en/content/articlelanding/2018/ra/c8ra00756j#!divAbstract)


## getting printer running from fresh Raspbian Buster Lite

1.  install fresh Raspbian Buster with Desktop
2.  get an Epson XP-440 printer
3.  install CUPS, gutenprint, and epson drivers
    ```shell
    sudo apt-get install cups printer-driver-gutenprint escputil
    ```
