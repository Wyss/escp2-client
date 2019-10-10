# escp2-client
Create ESC-P2 commands for Epson Printers

See paper describing the method at DOI: [10.1039/C8RA00756J](https://pubs.rsc.org/en/content/articlelanding/2018/ra/c8ra00756j#!divAbstract)


## getting printer running from fresh Raspbian Buster Lite

1.  Install fresh Raspbian Buster with Desktop
2.  Get an Epson XP-440 printer
<!-- 3.  Install CUPS -->
    <!-- ```shell -->
    <!-- $ sudo apt-get install cups -->
    <!-- ``` -->
4.  Download Gutenprint 5.2.11:
    ```shell
    $ cd ~/Downloads
    $ wget https://sourceforge.net/projects/gimp-print/files/gutenprint-5.2/5.2.11/gutenprint-5.2.11.tar.bz2
    ```
5.  Unzip the file into ~/gutenprint & install
    ```shell
    $ tar xvjf gutenprint-5.2.11.tar.bz2
    $ mv gutenprint-5.2.11/ ~/gutenprint
    $ cd ~/gutenprint/
    $ ./configure
    $ make
    $ sudo make install
    ```
6.  Install ESC/P2 Client
    1. From [http://github.com/wyss/escp2-client](http://github.com/wyss/escp2-client), clone the repo or download/unzip it.
    2. `cd` into the excp2-client folder (it can be located anywhere)
    3. Install required python modules
        ```shell
        $ pip3 install -r requirements.txt
        ```
7.  Run the program:
    - GUI
        ```shell
        python3 main_gui.py
        ```
    - Commandline
        ```shell
        python3 main_commandline.py
        ```
