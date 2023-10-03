<h1 align="center"><b><i>Raspberry PiKali</i></b></h1>

In this project, I'll guide you through setting up a mini portable pentesting environment using a Raspberry Pi 4B. It could be interesting if, somehow, you couldn't bring a whole laptop for a pentest !

<img alt="Kali" width="500px" src="https://github.com/IbrahimBenHariz/Raspberry-PiKali/blob/main/Ressources/PiKali.jpg"/></br>

## Prerequisites
Before you begin, ensure you have the following :</br>
Note : the links are totally subjective.

- **Raspberry Pi** : [Raspberry Pi 4B 4Go](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/)
- **Touchscreen for Raspberry** : [5inch LCD Touchscreen](https://www.amazon.com/Waveshare-Raspberry-Resistive-Interface-Rapsberry-pi/dp/B00TIA0PMQ/ref=as_li_ss_tl?ie=UTF8&qid=1495719070&sr=8-11&keywords=raspberry+pi+touchscreen+5+inch&linkCode=sl1&tag=nt-2017-20&linkId=b612c2f6693a10a26d092bac273ea59c)
- **Bluetooth Keyboard** : [Foldable Bluetooth Keyboard](https://www.amazon.com/Artciety-Foldable-Bluetooth-Keyboard-Pocket-Sized/dp/B0BN1SFZTC/ref=sr_1_5?crid=NRJ315NUC1U1&keywords=fold+keyboard+with+touchpad&qid=1695574484&sprefix=fold+keyboard%2Caps%2C161&sr=8-5)
- **SD Card (16Go Minimum)**

## Download Kali ARM Image
The images for ARM architecture can be found on the official Offensive Security website. Downloads are available via Torrent or the classic way with a simple image file.

Visit https://www.kali.org/get-kali/#kali-platforms to download the appropriate file for your Raspberry Pi.
</br>

I selected the ["Kali Linux Raspberry Pi 2 (v1.2), 3, 4, and 400 (64-bit)"](https://kali.download/arm-images/kali-2023.3/kali-linux-2023.3-raspberry-pi-arm64.img.xz) specifically, please don't forget to check the file hash !

## Prepare the "Bootable" SD Card
The easiest way in my opinion, is using Balena : you select the file, the target and you let the software do the work for you.

Once [Balena](https://etcher.balena.io/) is installed and launched, choose the downloaded image of kali and insert your SD card as the "target" to initiate the copying process. This may take some, 10 minutes for me.

<img alt="Kali" width="500px" src="https://github.com/IbrahimBenHariz/Raspberry-PiKali/blob/main/Ressources/Balena.png"/></br>

## Kali Linux Installation
Note : Be aware that you will need a screen and a wired keyboard for this step.

There's virtually nothing to do for the installation itself

Simply insert the SD card into your Raspberry Pi and power it on.
After a few moments, Kali Linux will appear on the login screen. Insert, start, and wait a little bit ! Simple, right ?

Default Credentials :
> User : kali</br>
> Password : kali

Of course, changing this password will be the first thing to do once the session is open.
You can easily do this by opening a terminal and entering the command :
```yaml
passwd
```

Also here is the command to change the keyboard layout, I had this issue because the default for Kali is qwerty and I am using azerty !
```yaml
sudo dpkg-reconfigure keyboard-configuration
```

## Touchscreen & Driver Installation
I have found this driver provided by LCD wiki that is compatible : https://github.com/lcdwiki/LCD-show-kali

```yaml
sudo rm -rf LCD-show-kali
git clone https://github.com/lcdwiki/LCD-show-kali.git
chmod -R 755 LCD-show-kali
cd LCD-show-kali/
# In case of 5inch HDMI Display(Resistance touch)(MPI5008)
sudo ./LCD5-show
```

After that the output on your screen of the raspberry should be different...... more... squared !</br>
Now it's [Plug & Play](http://www.lcdwiki.com/5inch_HDMI_Display) time and you are ready to use the Raspberry PiKali !

## Last Steps & Fixes
I had an issue with the Bluetooth not working anymore after the installation of the screen driver, it was reported in the github of [LCD wiki](https://github.com/lcdwiki/LCD-show-kali/issues/18)

To fix this issue I added this line ...
> dtoverlay=miniuart-bt

... at the end of "config.txt" in the /boot directory. Also be careful because I realized that depending the version of Kali the name of the "config" file could be different.

Don't forget to update your machine :
```yaml
sudo apt update
sudo apt full-upgrade -y
```

## Reach Out To Me <img alt="Contact Icon" width="40px" src="https://github.com/IbrahimBenHariz/IbrahimBenHariz/blob/main/PortfolioResources/ReachOutToMe.png"/>

[<img alt="LinkedIn" align="left" width="45px" src="https://github.com/IbrahimBenHariz/IbrahimBenHariz/blob/main/PortfolioResources/LinkedInIcon.svg"/>][linkedin]
[<img alt="Outlook" align="left" width="48px" src="https://github.com/IbrahimBenHariz/IbrahimBenHariz/blob/main/PortfolioResources/OutlookIcon.svg"/>][outlook]
[<img alt="Discord" align="left" width="47px" src="https://github.com/IbrahimBenHariz/IbrahimBenHariz/blob/main/PortfolioResources/DiscordIcon.svg"/>][discord]
[<img alt="Reddit" align="left" width="48px" src="https://github.com/IbrahimBenHariz/IbrahimBenHariz/blob/main/PortfolioResources/RedditIcon.png"/>][reddit]
[<img alt="Hack The Box" align="left" width="48px" src="https://github.com/IbrahimBenHariz/IbrahimBenHariz/blob/main/PortfolioResources/HackTheBoxIcon.svg"/>][hackthebox]
[<img alt="Try Hack Me" align="left" width="50px" src="https://github.com/IbrahimBenHariz/IbrahimBenHariz/blob/main/PortfolioResources/TryHackMeIcon.png"/>][tryhackme]
[<img alt="Credly" align="left" width="48px" src="https://github.com/IbrahimBenHariz/IbrahimBenHariz/blob/main/PortfolioResources/CredlyIcon.svg"/>][credly]

[kali]: https://www.youtube.com/watch?v=l0JgWilK6ok
[linkedin]: https://www.linkedin.com/in/ibrahim-benhariz
[outlook]: mailto:ibrahim.benhariz@outlook.com
[discord]: https://discord.com/users/1111590525066297464
[reddit]: https://www.reddit.com/user/IbrahimBenHariz
[hackthebox]: https://app.hackthebox.com/profile/1525863
[tryhackme]: https://tryhackme.com/p/IbrahimBenHariz
[credly]: https://www.credly.com/users/ibrahim-ben-hariz
[VM?]: https://techie-show.com/what-is-a-virtual-machine/
