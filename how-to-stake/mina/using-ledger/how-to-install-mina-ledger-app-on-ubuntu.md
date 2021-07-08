# How to install Mina Ledger app on Ubuntu

1. Open Terminal by pressing Ctrl+Alt+T. You can find a short guide of terminal commands for beginners [here](https://ubuntu.com/tutorials/command-line-for-beginners#3-opening-a-terminal).

2. Install python3:

```text
sudo apt-get install python3
```

3. Install pip3 package-management system:

```text
sudo apt-get install python3-pip
```

4. Install prerequisite libraries:

```text
sudo apt-get install libudev-dev libusb-1.0-0-dev python-dev virtualenv
```

5. Install Python tools for Ledger Blue, Nano S and Nano X:

```text
sudo pip3 install ledgerblue
```

6. Go to a [Ledger App Mina page](https://github.com/jspada/ledger-app-mina/releases)[.](https://github.com/jspada/ledger-app-mina/releases%5D.) You will see a list of Ledger App Mina releases. The current newest version is Ledger App Mina 1.0.2. Click on it. Then scroll down this section to "Assets" subsection at the bottom. Click on `ledger-app-mina-1.0.2-0-g843e809c.tar.gz` button and download the archive.

7. In the Terminal command line, go to the directory you just downloaded the archive. If you know how to do this, you don't need to read this point to the end.

To do this, go to this directory using the File Explorer, right click on the `ledger-app-mina-1.0.2-0-g843e809c.tar.gz` file and click on the "Properties" option. Go to a "Location" field of a "Basic" tab and double-click on the path you find there. Then copy this path by the right mouse click and "Copy" option or just use "Ctrl+C" keyboard combination. Path is copied to the clipboard. Then go to the Terminal window and paste the path with "cd" \(that means "change directory"\) into the command line. For example, if you downloaded the archive into `/home/cryptain/Downloads/`, your command to enter is the following:

```text
cd /home/cryptain/Downloads/
```

The Terminal will show that you jumped to the `/home/cryptain/Downloads/` directory from the directory you have been previously in.

8. Get your hash:

```text
sha256sum ledger-app-mina-1.0.2-0-g843e809c.tar.gz
```

Terminal will show you a table. Copy a set of numbers and letters from the HASH column and paste it to a text file. It is your checksum to verify that you use correct app.

9. Go to the Ledger App Mina 1.0.2 page or the release page you have downloaded in the step \#6, copy the SHA256 checksum from the bottom column \(corresponding to the `ledger-app-mina-1.0.2-0-g843e809c.tar.gz`\) and also paste it to your text file to compare these checksums. If they are the same, you use the correct version of the app and feel free to proceed the next step.

10. Extract the archive. For ease, you can unzip the archive into the same directory as the .tar.gz file. After the extraction, you will see the `ledger-app-mina-1.0.2-0-g843e809c` folder in the directory.

You can extact the archive using Archive Manager by double clicking on the `ledger-app-mina-1.0.2-0-g843e809c.tar.gz` and clicking on "Exctract" button or using the Terminal command:

```text
tar xvzf ledger-app-mina-1.0.2-0-g843e809c.tar.gz
```

Then an output is the following:

```text
ledger-app-mina-1.0.2-0-g843e809c/README.txt
ledger-app-mina-1.0.2-0-g843e809c/install.sh
ledger-app-mina-1.0.2-0-g843e809c/uninstall.sh
ledger-app-mina-1.0.2-0-g843e809c/mina_ledger_wallet
ledger-app-mina-1.0.2-0-g843e809c/bin/app.hex
```

11. Open the `ledger-app-mina-1.0.2-0-g843e809c` directory in the Terminal. To do this, copy the path to this directory and paste it into the Terminal using "cd" command, for instance:

```text
cd /home/cryptain/Downloads/ledger-app-mina-1.0.2-0-g843e809c
```

12. \(optional\) If you installed some version of Mina app before, remove it:

```text
./uninstall.sh
```

13. Launch the installation script:

```text
./install.sh
```

14. After you receive an output like this:

```text
Please unlock your Ledger device and exit any apps (press any key to continue)
Generated random root public key : b'04e95715d4813ab98c92833da9b169d3ff6ee11a4f94a465503cc91e77aaea688d45a0449f41bfaa2a1a789730e72d0ace759ca7c2b8a12e82c94cda61530cc363'
Using test master key b'04e95715d4813ab98c92833da9b169d3ff6ee11a4f94a465503cc91e77aaea688d45a0449f41bfaa2a1a789730e72d0ace759ca7c2b8a12e82c94cda61530cc363'
```

Your connected Ledger Nano S will show you

```text
< X Deny unsafe manager >
```

Click left until you see an option

```text
< ✓ Allow unsafe manager >
```

15. Ledger will show you

```text
< M Install app Mina >
```

Click left until you see an option

```text
< ✓ Perform installation >
```

and select it. Enter your Ledger PIN.

16. If the installation was successful, you will see the Mina logo among your Ledger apps. Also, the execution in the Terminal will be finished and you will see the opened directory of your Mina app in the Terminal.

17. Install the command-line wallet:

```text
sudo cp ./mina_ledger_wallet /usr/local/bin/
```

18. Now installation of the Ledger is completed, and we need a wallet to stake Mina from. There are four options to do this:

1\) wallet of own node

2\) third-party wallet such as:  
2.1\) Desktop browser wallets \(Clorio wallet, Auro wallet\),  
2.2\) Linux/Windows/OS X app wallets \(Clorio wallet\),  
2.3\) Android or iOS app wallets \(Staking-Power wallet, Auro wallet\).

Please choose a wallet you would like to use and follow the corresponding guides below:

{% page-ref page="how-to-stake-mina-from-clorio-browser-and-desktop-wallet-using-ledger.md" %}

{% page-ref page="how-to-stake-mina-from-auro-browser-and-mobile-wallet-using-ledger.md" %}







