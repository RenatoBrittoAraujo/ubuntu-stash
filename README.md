# Ubuntu Stash

An ubuntu program. 

1. You login to it (via password) and SSOs into some cloud storage tools, like NextCloud, Google Drive, AWS.
2. It uses your private key to decrypt the filesystem there.
3. It syncs some specific things with your local device.
   1. The command `dpkg --get-selections > f` creates a file with all you packages, which you many seamlessly port to a new machine via a `dpkg --set-selections < f; apt-get dselect-upgrade`.
   2. Can have custom configured apps to install. TOR, VPNs...
   3. Can also set some customization options so you only have to perform it once. Wallpaper, OhMyPosh, Terminal colors...
   4. Can include your scripts in `~/scripts` so you can run anytime you want. Examples can include: Download and burn Ubuntu ISO in flashdrive in a single command, scraps data...
   5. Can install password manager + include some automatic signon experience, so you may open a tab already signed in the app you want right after Stash setup.
   6. Can make your system acessible via a PL + SSH with some cloud provisioning, such as AWS + terraform.

Focus here is privacy, so all files will be encrypted with the highest degree of safety and can only be interpreted by you on a safe system. A module of encryption will sit inbetween cloud and local.

A good feature is to have a sync system, which will save and manage versions of your multiple systems and you can sync with any of them easy. This feature add complexity and can be skipped for an MVP. 

## Viability

There are several tools which makes this easy, a lot of libraries and packages may be levraged.

## Usability

### User downloads

```
$ sudo apt install git
$ git clone renatobrittoaraujo/ubuntu-stash
$ cd ubuntu-stash
```

### User installs 

```
$ sudo install.sh
```

An installer would be important, and it would do a couple of things:
1. Install dependencies
2. Put executable on user bin.

### User sets up 

```
$ ubuntu-stash

> What is your passphrase? (for decryption and encryption)
ball cat

> Would you like to login to GOOGLE DRIVE?
n

> Would you like to login to AWS?
y

> [AWS] AWS_ACCESS_KEY_ID = ??
ABC123

> [AWS] AWS_SECRET_KEY = ??
DEF456

> [AWS] AWS_REGION = ??
sa-east-1

> [AWS] Logged in!

> Would you like to login to NEXTCLOUD?
y

> [NEXTCLOUD] Installing...

> [NEXTCLOUD] What is your provider?
xvideos.com

> [NEXTCLOUD] What is your provider username?
jose

> [NEXTCLOUD] What is your provider password?
123

> [NEXTCLOUD] Logged in! NextCloud file sync has been initialized in `~/NextCloud/`.

> Would you like to install your apt/snap packages from cloud?
y

> [APT/SNAP] Installing...
> [APT/SNAP] Installed!

> Would you like to set your `.bashrc` to cloud configs?
y

> [BASHRC] Set!

> Would you like to setup your system's theme (terminal theme, wallpaper, system colors, ...)?
y

> [THEME] Wallpaper set!
> [THEME] Terminal configured!
> [THEME] System Apparence set!

> Would you like to setup your password manager?
y

> [PASSWORD MANAGER] Installing...
> [PASSWORD MANAGER] Installed! Launching it for you to login...

> Would you like to install your webapp launcher with SSO / automatic login?
y

> [WEBAPP LAUNCHER] Installed!

> Would you like to sync this system's folders with snapshot from AWS?
y

> [SNAPSHOTS] Synced!

> Would you like to enable automatic syncing / backups?
y

> [SYNC] Give your system a name:
laptop-thinkpad

> [SYNC] Name 'laptop-thinkpad' already exists. Give your system another name:
laptop-thinkpad-2

> [SYNC] Enabled!

> Would you like to setup your `~/scripts/` folder?
y
 
> [SCRIPTS] Set up!

> [SCRIPTS] Would you like to check out your custom configuration / installation scripts in `~/scripts/setup/`?
y

> [SCRIPTS - TOR.sh] Would you like to run 'TOR.sh'?
y

> [SCRIPTS - TOR.sh] > installing tor 
> [SCRIPTS - TOR.sh] > setting up things
> [SCRIPTS - TOR.sh] > hey it's installed :)

> Would you like to run 'VPN.sh'?
y

> [SCRIPTS - VPN.sh] > installing...

> [SCRIPTS - VPN.sh] ERROR - Script has exited with status code 3!
> [SCRIPTS - VPN.sh] ERROR - All logs can be found at `.stash/logs/38fbf8b3-ea28-460e-b9e3-5374073d8ba7.txt`

> [SCRIPTS - SSH_SETUP.sh] Would you like to run 'SSH_SETUP.sh'?

> [SCRIPTS - SSH_SETUP.sh] > provisioning AWS proxy to this machine using terraform
> [SCRIPTS - SSH_SETUP.sh] > setting up ssh
> [SCRIPTS - SSH_SETUP.sh] > port 22 open
> [SCRIPTS - SSH_SETUP.sh] > ssh is now accessible!
> [SCRIPTS - SSH_SETUP.sh] > DNS: 1-23-43-69-whatever.sa-east-1.amazonaws.com
> [SCRIPTS - SSH_SETUP.sh] > IPV4: 1.23.43.69
> [SCRIPTS - SSH_SETUP.sh] > IPV6: d340:eb9a:eac4:6358:2109:15ed:128e:2d50

> You are all setup!
```

### User sets up 

```
$ ubuntu-stash stash

> Would you like to stash to 'laptop-thinkpad-2'?
n

> To which would you like to stash?
> [1] laptop-thinkpad
> [2] laptop-thinkpad-2
> [3] desktop-1
1

> Stashing your system to the cloud...
> All you configuration have been stashed!
```

