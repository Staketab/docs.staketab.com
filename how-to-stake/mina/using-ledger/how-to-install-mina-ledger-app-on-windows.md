# How to install Mina Ledger app on Windows

1. Download [python](https://www.python.org/ftp/python/3.9.1/python-3.9.1-amd64.exe)[.](https://www.python.org/ftp/python/3.9.1/python-3.9.1-amd64.exe%5D.)

2. Launch the `python-3.9.1-amd64.exe` file and install python. For fast installation, you can click on "Install now" button in a window after _.exe_ installer launch. Then python will be installed to the predefined directory on the system disk. For custom installation directory and options, click on "Customize installation".  
Note: check "Add Python 3.9 to PATH" checkmark at the bottom of an installation welcome screen.

3. Press "Windows + R" buttons combination, enter `powershell.exe` into the field appeared, then press "Enter". Windows PowerShell window appears.

4. Paste the following command into the PowerShell command line to download necessary lib:

```text
pip3 install ledgerblue
```

5. Go to a [Ledger App Mina page](https://github.com/jspada/ledger-app-mina/releases)[.](https://github.com/jspada/ledger-app-mina/releases%5D.) You will see a list of Ledger App Mina releases. The current newest version is Ledger App Mina 1.0.2. Click on it. Then scroll down this section to "Assets" subsection at the bottom. Click on `ledger-app-mina-1.0.2-0-g843e809c.zip` button and download the archive.

6. In the PowerShell command line, go to the directory you just downloaded the archive. To do this, go to this directory using the File Explorer, right click on the `ledger-app-mina-1.0.2-0-g843e809c.zip` file and click on the "Copy as path" option. Path is copied to the clipboard. Then go to the PowerShell window and paste the path with "cd" command before it \(that means "change directory"\) into the command line. For example, if you downloaded the archive into C:\Downloads directory, your command to enter is the following:

```text
cd C:\Downloads
```

The PowerShell will show that you jumped to the `C:\Downloads` directory from the directory you have been previously in.

For the basic Windows commands, please see this [guide](https://www.digitalcitizen.life/command-prompt-how-use-basic-commands/)[.](https://www.digitalcitizen.life/command-prompt-how-use-basic-commands/%5D.)

7. Get your hash:

```text
Get-FileHash -Path ledger-app-mina-1.0.2-0-g843e809c.zip
```

PowerShell will show you a table. Copy a set of numbers and letters from the HASH column and paste it to a text file. It is your checksum to verify that you use correct app.

8. Go to the [Ledger App Mina 1.0.2 page](https://github.com/jspada/ledger-app-mina/releases/tag/v1.0.2) or the release page you have downloaded in the step \#5, copy the SHA256 checksum from the bottom column \(corresponding to the `ledger-app-mina-1.0.2-0-g843e809c.zip`\) and also paste it to your text file to compare these checksums. If they are the same, you use the correct version of the app and feel free to proceed the next step.

9. Go to the directory you have downloaded `ledger-app-mina-1.0.2-0-g843e809c.zip` and extract the archive. For ease, you can unzip the archive into the same directory as the _.zip_ file. After the extraction, you will see the `ledger-app-mina-1.0.2-0-g843e809c` folder in the directory.

10. Open the `ledger-app-mina-1.0.2-0-g843e809c` directory in the PowerShell. To do this, copy the path to this directory and paste it into the PowerShell using "cd" command, for instance:

```text
cd C:\Downloads\ledger-app-mina-1.0.2-0-g843e809c
```

11. \(optional\) If you installed some version of Mina app before, remove it:

```text
python3 -m ledgerblue.deleteApp "--targetId" "0x31100004" "--appName" "Mina"
```

12. Install Mina app:

```text
python3 -m ledgerblue.loadApp "--path" "44'/12586'" "--appFlags" "0x240" "--tlv" "--targetId" "0x31100004" "--targetVersion=1.6.0" "--delete" "--fileName" "bin/app.hex" "--appName" "Mina" "--appVersion" "1.0.0" "--dataSize" "64" "--icon" "010000000000ffffffffffffffffffeff7c7e393c9b3cdb3cdb3cdb3cdb3cd33cc799effffffffffff"
```

{% hint style="warning" %}
If after running the command you encounter an error like:

`Python was not found.`

You may try to replace `python3` with `py` in the command above.
{% endhint %}

13. After you receive an output like this:

```text
Generated random root public key : b'04e95715d4813ab98c92833da9b169d3ff6ee11a4f94a465503cc91e77aaea688d45a0449f41bfaa2a1a789730e72d0ace759ca7c2b8a12e82c94cda61530cc363'
Using test master key b'04e95715d4813ab98c92833da9b169d3ff6ee11a4f94a465503cc91e77aaea688d45a0449f41bfaa2a1a789730e72d0ace759ca7c2b8a12e82c94cda61530cc363'
```

your connected Ledger Nano S will show you

```text
< X Deny unsafe manager >
```

Click left until you see an option

```text
< ✓ Allow unsafe manager >
```

Select the option.

14. Ledger will show you

```text
< M Install app Mina >
```

Click left until you see an option

```text
< ✓ Perform installation >
```

and select it. Enter your Ledger PIN.

15. If the installation was successful, you will see the Mina logo among your Ledger apps. Also, the execution in the PowerShell will be finished and you will see the opened directory of your Mina app in the PowerShell.

16. Now installation of the Ledger is completed, and we need a wallet to stake Mina from. There are four options to do this:

1\) wallet of own node

2\) third-party wallet such as:  
2.1\) Desktop browser wallets \(Clorio wallet, Auro wallet\),  
2.2\) Linux/Windows/OS X app wallets \(Clorio wallet\),  
2.3\) Android or iOS app wallets \(Staking-Power wallet, Auro wallet\).

Please choose a wallet you would like to use and follow the corresponding guides below:

{% page-ref page="how-to-stake-mina-from-clorio-browser-and-desktop-wallet-using-ledger.md" %}

{% page-ref page="how-to-stake-mina-from-auro-browser-and-mobile-wallet-using-ledger.md" %}







