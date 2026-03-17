# Project for April: Zammad Quadlets
**As you may have noticed when looking at my Repos, there's a new one. This is for my April project which I'm already working on. Converting the Compose of the Ticket System Zammad into fully working Quadlets files. At the time of writing this (14.03.2026), I already got the containers running and am only facing a problem with the Nginx of Zammad loading the UI.**

## Current project ##
First of all, I did not forgot about the project for march.
Funny thing is, I accidently tested all of the playbooks I have by now.

You may know that I had two systems running on my main PC.
Red Hat Enterprise Linux and Arch, from which I mainly used Arch.

Because of that, I only had limited disk space on my SSD which caused some problems.
For example, I had to change the location of podman images and volumes to my HDD, which for some reason caused DNS issues between containers in the same network.

So I decided to delete the RHEL partitions with cfdisk and give the free space to the root partition of arch.

I know I know, stupid mistake.

After realizing it's not that easy, I went to look for solutions and something promising was using GParted.

Burned it to a USB-Drive, booted into the live system and it looks good.

One guide I found told me to basically make a backup to my hdd, delete all disks and created new ones. One for EFI, one for swap and one as the root partition.

Only after all that went sucessfully I booted into arch live and restored the backup... Well that didn't work.

I had to reinstall my whole system and what better opportunity to test the Ansible Playbooks when not in production.

Many errors accoured which I semi-professional fixed and the playbooks ran through.

Many things needed to be set up after that manually.

Some because of my NVIDIA GPU (which I will not include in the main Playbook but maybe as a seperate snippet), and some I just didn't think about.

Of course I was just happy to have a running system again so I went to bed since it was already pretty late.

On the next day, or maybe the day after, I decided to create a dedicated Repository for the project called [Arch_Linux_Post-Install_Automation
](https://codeberg.org/Spoljarevic/Arch_Linux_Post-Install_Automation) and document all the errors I got in form of Issues there.

So yeah, I'm still working on it and it should finish in time.

## What's the project for April? ##
I always want to do things that are usefull.
And Zammad is my beloved Ticket system that I already used in the past.
Official hosting can get pretty expensive tho, so self-hosting is the way to go.

If you're not familiar with a ticket system, let me tell you it's the industry standard in IT.

Customer has a problem, let him open a ticket! In there you can document everything you did aswell as the time you spent.
It's kinda like GitHub/GitLab/Codeberg Issues, but on crack.

In a company I used to work in, we used Tanss as the ticket system.
Pretty solid choice with many things you can configure.

Problem is, it's neither open source nor can you self-host it.
Well you can, if you spend a shit ton of money for it.

So I wanted a new system, one that goes along with my ideals, and that's Zammad.

It was created in 2016 by former founder of OTRS, Martin Edenhofer.
You may already thing, wait, that sounds german, and it is.
Zammad is based in Berlin, Germany.

Zammad is leaner, more modern, and more user-friendly then most other systems while giving you full control over whatever you want to do.
After all, the source code is freely available on GitHub.


I used to run it via podman compose, which worked pretty good, but it's not a real sysadmin way.
You don't want to go into your server and start services like zammad manually because it's not systemd.
You also don't want to install it bare metal, so what now?

The answer to that are Podman Quadlets, run containers rootless (if you like) and more importantly, via systemd.
Let the servers start themself you may say.

And that's exactly what I will do.

## Technical specs ##
Zammad consists of 10 Containers in total.
- Backup
- Elasticsearch
- Init
- Memcached
- Nginx
- Postgresql
- Railsserver
- Redis
- Scheduler
- Websocket

So we need a .container file for every single one of those services.
We also need two more files, a zammad.network file for the containers to talk to each other and a zammad.pod file.
This one handels everything for us like port exposure and systemd.

Instead of starting 10 containers, we only start zammad-pod.service and be happy.

I already created all of them and they do work in theorie, if not for a little DNS issue.

You see, the auto generated nginx file tells 2 things we need to keep an eye on. Railsserver and the variable railssver_url.
First one points to 127.0.0.1 and works perfectly, the variable on the other hand uses the DNS name railsserver, which for some reason doesn't work.

I admint not having spend to much time into this issue since I was already happy that all containers ran after a lot of troubleshooting, but that's why I make a project out of it, right?

All files are already op on my Codeberg Repo [Zammad-Podman-Quadlets](https://codeberg.org/Spoljarevic/Zammad-Podman-Quadlets) and can be cloned and looked into.

I made a short README file explaining that to avoid this issue, I recommend mounting ``zammad-storage`` to a local path and changing the nginx config.

But of course that's just temporary and I'm going to fix this issue soon.

The wiki is also work in progress and will be finished with the rest of it next month.

## How you can help ##
If you have any experience with DNS and Podman, I'll gladly accept your help.
Just clone the Repo, do your magic and open a pull request.

I'll then look into it, test it on different VMs and if it works, merge it into the master branch.
Of course you'll get mentioned as a contributor and might even recieve some XMR as kind of a bug bounty lol.

## The end ##
That's it for today, hope you enjoyed it.

Don't feel pressured now to do anything, the call for help is more of me liking the thought of fixing something together as a open source community rather then me being desperate for it.
Sure, it might need some time, but I can very well figure it out myself.

Let me know what you think about the project for march.
I also take suggestions on what future projects could be if you have any ideas and remember... **Stay private. Stay root**!
