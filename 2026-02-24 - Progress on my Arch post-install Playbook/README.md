```
Author: Luca Matteo Spoljarevic
Contact: git@spoljarevic.info
My new website: https://spoljarevic.sh
Socials: https://socials.spoljarevic.sh
Projects: https://projects.spoljarevic.sh
Date created: 2026-02-24
Last changed: 2026-02-24
```

# Greetings everyone!
My last post, where I talked about pretty much everything in life, is now 13 days old.

This time I want to talk about one topic, and one topic only... **Ansible**.

More specificly my Archinstall playbook.
Now don't get wrong ideas, this playbook is not there to replace the archinstall Script from Arch Linux.
This is more of a post-install playbook that is very badly named...

So what's new and what can you expect?

## My goal for March ##
As you might know, this months project is documentation for my [Codeberg](https://codeberg.org/Spoljarevic) Repos.
I've made okay progress and should be able to finish it in time.

But you don't care about that, do you?
You're here for the project in March.

A complete overhaul of my archinstall playbook.
I want to talk about it a bit here, so this post is dedicated only to that!

## The current playbook and why it needs an overhaul ##
The current playbook can be found [here](https://codeberg.org/Spoljarevic/Ansible/src/branch/master/installation/archinstall.yml).

It installs a bunch of software. Some isn't even needed but many are not even there.
Why would someone use this playbook if he needs to install half of the software manually huh?
But even if we ignore what pacman installs, Flatpakl and yay are not better.

### Flatpak ###
Discord is already in the official Repo from Arch.
I know it has some problems with updates, but rather that then Flatpak.
Besides, Vesktop is supirer anyway and will be installed too.

 ### yay ###
Yay installs a lot of software.
But for example onlyoffice and vscodium are not needed anymore.

Of course yay stays in the new playbook to install software like cmatrix-git, tofi and snapd.
But what's with the other software you may ask. Let's take a look at those!

### Making use of other Repos
In the new playbook, two Repos will be installed besides the official Arch Repo.
That are CachyOS and BlackArch.

While the BlackArch doesn't do much at the moment, the CachyOS Repo is really usefull.
With that, we can install the Proton applications, Vesktop, the Zen Browser and Davinci Resolve.

No need for the Aur anymore... well at least not for most of the software.

## Why Ansible? Can't I just do it by hand or via Bash Script? ##
At the beginning, when we had Ansible for a few weeks in school, I tought that was just a useless piece of software.

Only a year or so later I saw the potential.
You can do so much more with it then for example with Bash, and that while having way less of a headache and much more control and insights.

For example, if you are in Ansible at spep 6. It wouldn't start at the beginning again in case of an error.
When running it again, it sees the changes that are already done and just skips them.

Besides, I find it easier to use then Bash Scripts and thanks to community plugins, you often don't need extra software to do things.

For example in my Bash script for converting images to sixel, the software ``bc`` was needed to calculate size.

Ansible has stuff like that build in, no need to install more bloat.

Those are just a few examples, but Ansible can do so much more.

If you are a Sysadmin like me, or just care about your Homelab, this tool **is a must*+ to learn!

## What will be implemented? ##
I want to automate as much as I can.
What's already there is showed later, but what I can promise you is that it'll save you many many hours while being error free.
Things that are missing which I know I want to implement are changing ownership, mounting external volumes, pull images like wallpapers and stuff, hardning of the OS and much more!

## How can I suggest ideas that I think are missing? ##
I'm more then happy to take ideas into consideration.
Just create an issue [here](https://codeberg.org/Spoljarevic/Ansible/issues).
Please add ``The Archinstall Playbook - Building it from ground`` as the Milestone and ``Updating the archinstall playbook - A full Arch Linux post-install playbook`` as the Project.

When doing that, the Issue will automatically be assigned to ``Community Ideas`` inside the Project.

This helps me get a structured overview of everything y'all want to see in the final product.

## I don't see it in the Repo, so where is it? ##
Don't worry, you're not blind.
You are probably just looking in the wrong branch.

Just change the branch from master to development and go to ``installation/Arch Linux/post-install``.
There you're finding everything you need.

But if that's to complicated, then you can follow [this link](https://codeberg.org/Spoljarevic/Ansible/src/branch/development/installation/Arch%20Linux/post-install).

I promise you won't get any maleware when clicking on that link, no need to check it for yourself ;D

## What is already there? ##
Currently, I'm working on these snippets:
- Installation
    - AurInstaller
    - flatpakInstall
    - pacmanInstall
    - snapInstall
- Repos
    - addBlacharchRepo
    - addCachyosRepoToArch
- Random
    - gitclone
    - sshkeys

These will be implemented into one single Playbook at the end.
Except the **gitclone.yml** playbook, everything is tested and working.
But more to that later, now we are gonna take a closer look on each of those files.

## Installation
### AurInstaller ###
The collection [kewlfft.aur.aur](https://galaxy.ansible.com/ui/repo/published/kewlfft/aur/) will be used to install AUR Packages.

After installing the base packages via pacman, Ansible will create a new user called ``aur_builder`` and change his permmissions to execute sudo commands without a password.

This follow the official documentation.

Then yay will be installed via makepkg and when that's done, packages will be installed with the kewlfft.aur.aur collection and yay.

### flatpakInstall ###
The playbook first ensures that flatpak is installed.
After that, it will use ``command`` and ``args: creates:`` to add the official Flathub Repo to it.
Now everything it needs to do is to install the software you choose to install via ``flatpak:``.

### pacmanInstall ###
This one's self explanatory.
Packages are installed via ``ansible.builtin.pacman``.
It is important that the CachyOS and Blackarch Repo are installed before executing this playbook.

To automate this, just run the playbooks addBlacharchRepo.yml and addCachyosRepoToArch.yml.

In the final playbook, this will not be needed since those are going to be already implemented.

### snapInstall ###
Just like with flatpak, ansible first ensures that snapd is installed.
the AurInstaller Playbook already handels that so we should be safe.

It then enables and starts the socket with Ansibles builtin ``systemd`` tool.

Currently, the only software I need from snap is lunatask, but you  can add whatever you want to it.

## Repos ##
### addBlacharchRepo ###
This playbook is pretty simple.
Installs curl and gnupg and then procceds to download and execute the blackarch script which will add the Repository to pacman.
At last, pacman will be upated and you can go ahead and install everything your wannabe hacker heart desires.

### addCachyosRepoToArch ###
This one's a bit more complicated.
I always got an error when executing the official script, so I took it apart and made a playbook out of it.

First the variables are declared.
The CachyOS key, the keyserver, the pkg url's and the block that needs to be added to ``/etc/pacman.conf``.

Now we just need to receive the signed keys, locally sign them, Install the keyring and mirrorlist packages and at last add the CachyOS Repository to pacman.conf with the block we defined in the vars.

## Random ##
### gitclone ###
**This is not working at the moment!**

My goal was to clone all the Repos I use/maintain via ssh and put them into a dedicated folder that the playbook creates.
But I always ran into error when the playbook tried to clone them.

I know it sounds stupid was I just couldn't get why.

Now it's pretty obvious that I just can't clone the Repos without adding the SSH-Key from the machine to my Codeberg account.

Because of that, I'm gonna try to just download them via https and then change remote to ssh.

### sshkeys ###
Now that I look at it, this playbook is pretty easy.

It took me way to long to write tho.

I always got an error when trying to create a ssh-key with it.
That was because it couldn't find ssh-keygen even tho it was installed.

The solution was to just install ``python-cryptography`` and ``python-bcrypt`` to do the same job.
I was very happy to see it working after that.

## Sounds good, what happens now? ###
Well... I'm gonna try to collect more ideas. My own and yours.
When I think I'm done, I'll reset my VM to a snapshot that was made right after it's installation and execute every single playbook.
I expect them to succeed without any errors, but testing never hurts.
After that, they are gonna get combined into one single Playbook and we do the same thing again.

I want to have a playbook that is bullet proofed and does everything I'd need to do manually.

## Footer ##
If you read until here, I thank you from the bottom of my heart.
This project means a lot to me and I promise that it will succeed!

As always, feel free to message me on whichever plattform you prefer.
My socials Link is on top of this Blog post, from there if should be easy to find me.

If you see this Blog post on Codeberg, I'd like to inform you that I have an actual site for this now.
To take a look at this, just click on [this link](https://spoljarevic.sh/blog) or visit [https://spoljarevic.sh/blog](https://spoljarevic.sh/blog).

That's it for today!
Goodbye everyone and remember... **Stay private. Stay root.**
