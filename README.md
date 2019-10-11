# escp2-client
Create ESC-P2 commands for Epson Printers

See paper describing the method at DOI: [10.1039/C8RA00756J](https://pubs.rsc.org/en/content/articlelanding/2018/ra/c8ra00756j#!divAbstract)


## getting printer running from fresh Raspbian Buster Lite

1.  Install fresh Raspbian Buster with Desktop
2.  Get an Epson XP-440 printer
3.  Install CUPS and Epson printer drivers and Gutenprint
    ```shell
    $ sudo apt-get install cups driver-printer-escpr gutenprint
    ```
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
    $ sudo make
    $ sudo make install
    ```
6.  Install ESC/P2 Client
    1. From [http://github.com/wyss/escp2-client](http://github.com/wyss/escp2-client), clone the repo or download/unzip it.
    2. `cd` into the excp2-client folder (it can be located anywhere)
    3. Install required python modules
        ```shell
        $ pip3 install -r requirements.txt
        ```
7.  Add printer to CUPS:
    1. Open the cups files config
        ```shell
        sudo nano /etc/cups/cups-files.conf
        ```
    2. At the end of the file, add the case-sensitive line:
        ```shell
        FileDevice Yes
        ```
    3. Restart CUPS:
        ```shell
        sudo /etc/init.d/cups restart
        ```
    4. Open a browser and navigate to URL [http://localhost:631](http://localhost:631)
    5. Under the *Administrators* menu, click *Add Printer*. Log in with device credentials.
    6. Click *LPD/LPR Host or Printer* and type `file:/tmp/arbitrary.prn` and continue.  
    7. Name the printer, select *Epson* in the *Make* menu and continue. In the *Model* menu, select the corresponding model with `CUPS+Gutenprint v5.2.11(en)` in the name.  Continue and select default options.
7.  Make unprint executable
    ```shell
    sudo chmod +x ~/gutenprint/test/unprint
    ```
8.  Generate simple printer output
    1. Find a small text file to print.
    2. In the terminal, enter
       ```shell
       $ lp -d <printername> <smallfile>
       ```
       where <printername> is the name of the printer when added to CUPS earlier, and <smallfile> is the arbitrary small text file.
       -  This saves the output to `/tmp/arbitrary.prn` from when the printer was added to CUPS.
    3. Move the .prn file somewhere you can edit it, in `~/prn` for example:
       ```shell
       $ mkdir ~/prn
       $ cd ~/prn
       $ sudo cp /tmp/arbitrary.prn . && sudo chmod 777 arbitrary.prn && mv arbitrary.prn <newname>.prn
       ```
       where <newname>.prn is a readable descriptive name, (e.g. <newname> = xp-440 for the Epson Expression XP-440 printer).
8.  Run the program:
    - GUI
        ```shell
        python3 main_gui.py
        ```
    - Commandline
        ```shell
        python3 main_commandline.py
        ```
