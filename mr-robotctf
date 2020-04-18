# Tryhackme's Mr.Robot CTF
#### Our nmap scan yielded these results: 
![](../Downloads/img1.png)
#### So off to the webpage we go!
#### When we first load up the page, we get this command-line interface with a set of options: 
![](../Downloads/img2.png)
#### My first thought is to try to run commands such as whoami or ls but the only available commands are the ones listed:
* The prepare command brings us to a video
* The fsociety command brings us to a shorter video
* inform brings us to a set of images
* question brings us to another set of images
* wakeup brings us to a short clip from the Mr. Robot series
* join brings us to a terminal which has us enter our email

#### My second thought is accessing these images & videos and seeing what else is in the directories, but sadly: 
![](../Downloads/img3.png)
#### It's not allowed for any of the directories
#### I then decided to enter a random directory that I knew wouldn't exist to see what type of error message I would get and boom: 
![](../Downloads/img4.png)
#### It's a Wordpress blog!
#### I then checked the hints button on the CTF website and it just said robots, so I navigated to /robots.txt which shows what is accessible and what isn't on websites: 
![](../Downloads/img5.png)
#### Navigating to /key-1-of-3.txt will get us our first key
#### Navigating to /fsocity.dic will get us what appears to be a wordlist: 
![](../Downloads/img6.png)
#### A veeerrry long wordlist that is: 
![](../Downloads/img7.png)
#### And can I just question, how on Earth did fsociety get spelled wrong?
#### At first, I thought the wordlist was for subdirectories, and after about an hour of letting ffuf run, this was about all I discovered: 
![](../Downloads/img8.png)
#### So then I realized it may be a password list and I tried the obvious /login directory and ended up guessing the username would be Elliot since it's a Mr.Robot themed machine & brute forced it with the fsociety.dic file
#### And boom! Access granted: 
![](../Downloads/img9.png)
#### Now we can access all the media on the site: 
![](../Downloads/img10.png)
#### After navigating to the appearance > editor section, we can edit any of the PHP scripts on the website, which makes gaining access fairly simple: 
![](../Downloads/img11.png)
#### I chose to edit the 404 Template as this is what will pop up any time a directory isn't found, so for example: trying to access /jibberish-words would lead to us spawning a shell but you can choose any PHP script on here
#### After gaining our initial foothold, we gain an interactive shell, not only does this look better, it is also needed for some commands such as su: 
![](../Downloads/img12.png)
#### Key 2 found! But unfortunately we don't have the needed permissions to read the file: 
![](../Downloads/img13.png)
#### But! We do have the appropriate permissions to read the password.raw-md5 file: 
![](../Downloads/img14.png)
#### Next stop, [crackstation](https://crackstation.net) where there are pre-cracked hashes you can compare your hash to in order to see if it's been cracked before.
#### Guess what? 
![](../Downloads/img15.png)
#### I'm pretty sure this password was also in the fsocity.dic wordlist from earlier too
#### After using that password to gain access to the robot user, we're able to get the 2nd flag.
#### For the final flag, we need root access to the machine, this is the part I struggled with as I am not the most informed individual when it comes to privesc
#### To start off, I searched for files that have SUID set which is basically an owner's permission set to a file, so when a regular user runs it, it runs with the owner's permission and sometimes that owner is root: 
![](../Downloads/img16.png)
#### nmap with SUID? Seemed kinda odd to me, this basically means nmap runs with someone's permissions, perhaps root? 
![](../Downloads/img17.png)
#### The interactive mode was out of the norm for me: 
![](../Downloads/img18.png)
#### So you can run shell cmds with nmap's interactive mode and this will have someone else's permissions, but whose permissions? 
![](../Downloads/img19.png)
#### Boom, rooted, technically right? 
![](../Downloads/img20.png)
#### and there's our 3rd key!
#### Looping back though, I attempted to get linpeas on this machine by using a simple python server but for some reason, it wasn't working. Here's the output I was getting: 
![](../Downloads/img211.png)
#### Thinking it over though, I may have been able to get linpeas on the box through curl instead of wget.
#### But we are able to get linpeas on the machine with nmap since it runs with root's permissions, so IF we were able to run it once we gained our initial foothold, it would've detected & suggested the nmap route to rooting the box: 
![](../Downloads/img23.png)
#### I'm not entirely sure why it says "You can write SUID file", but there ya have it!


