# Using own Mina node

## How to install Linux? <a id="How-to-install-Linux?"></a>

We recommend to install Ubuntu as one of the most user-friendly Linux distributions. You can find guides how to install Ubuntu here:

* [How to install Ubuntu?](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)
* [How to install Ubuntu alongside Windows?](https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/)
* [How to install Ubuntu on virtual machine?](https://www.lifewire.com/install-ubuntu-linux-windows-10-steps-2202108)

If you prefer some another Linux distribution, the steps below are similar.

## How to stake Mina? <a id="How-to-stake-Mina?"></a>

### Launch terminal <a id="Launch-terminal"></a>

Click _Ctrl+Alt+T._

Linux terminal is opened. You can find a short guide of terminal commands for beginners [here](https://ubuntu.com/tutorials/command-line-for-beginners#3-opening-a-terminal%5D.).

### Create private key <a id="Create-private-key"></a>

At first, enter the following commands to install necessary packages:

```text
echo "deb [trusted=yes] http://packages.o1test.net release main" | sudo tee /etc/apt/sources.list.d/mina.list
sudo apt-get update
sudo apt-get install -y curl unzip mina-mainnet=1.1.5-a42bdee
```

Then install the key generator with the command:

```text
sudo apt-get install mina-generate-keypair=0.2.12-718eba4
```

### Generate the key:

When creating keys, you will be asked to create a password.

#### Option 1 with a package:

```text
mina-generate-keypair -privkey-path ~/keys/my-wallet
```

#### Option 2 using docker:

```text
docker run  --interactive --tty --rm --volume $(pwd)/keys:/keys minaprotocol/generate-keypair:0.2.12-718eba4 -privkey-path /keys/my-wallet
```

### Set necessary permissions:

```text
chmod 700 $HOME/keys
chmod 600 $HOME/keys/my-wallet
```

### Check private key <a id="Check-private-key"></a>

When checking the key, you will be asked to enter the password from it.

#### Option 1 with a package:

```text
mina-validate-keypair -privkey-path ~/keys/my-wallet
```

#### Option 2 using docker:

```text
docker run --interactive --tty --rm --entrypoint=mina-validate-keypair --volume $(pwd)/keys:/keys minaprotocol/generate-keypair:0.2.12-718eba4 -privkey-path /keys/my-wallet
```

In both cases, if everything is ok with your keys, you will receive a message:

```text
Verified a transaction using specified keypair
```

It means your keys have been verified.

Now let's write your public key to the server in the `.bashrc` file so that we don't export them again next time.

```text
echo 'export KEYPATH=$HOME/keys/my-wallet' >> $HOME/.bashrc
echo 'export MINA_PUBLIC_KEY=$(cat $HOME/keys/my-wallet.pub)' >> $HOME/.bashrc
source ~/.bashrc
```



