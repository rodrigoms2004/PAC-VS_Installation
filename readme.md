# PAC Installation on UBUNTU 18.04

How to install PAC in UBUNTU 18.04 and its issues

### Useful links

[Solution from](https://sourceforge.net/p/pacmanager/bugs/293/)

[PAC Download](https://sourceforge.net/projects/pacmanager/)

or

[PAC Download from repo](https://github.com/rodrigoms2004/PAC-VS_Installation/blob/master/pac_download/pac-4.5.5.7-all.deb)

### Installation 


Download PAC from Source Forge or from this repository 

Install it from command line

``` 
sudo dpkg -i pac-4.5.5.7-all.deb
```

Solve any dependencies using

```
sudo apt-get install -f
```

### Fixing it


Install its libs

```
sudo apt install libglib2.0-dev libpango1.0-dev libvte-dev libvte-2.91-dev dh-make-perl -y
```

#### Perl issue


To solve this issue 

*I was getting these errors:*
*MakeMaker FATAL: prerequisites not found.*
*ExtUtils::Depends not installed*
*ExtUtils::PkgConfig not installed*

Run 

```
sudo perl -MCPAN -e 'shell'
```

In Perl shell execute

```
install ExtUtils::Depends
install ExtUtils::PkgConfig
exit
```

Create the deb packages

```
dh-make-perl --cpan Gnome2::Vte --build
```

Install them

```
sudo dpkg -i libgnome2-vte*.deb
```

Remove some garbage

```
sudo find /opt/pac/ -name "Vte.so*" -exec rm {} +
```


Enjoy!