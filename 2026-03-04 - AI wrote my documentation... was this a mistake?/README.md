# AI wrote my documentation... was this a mistake?
**Why I let AI write documentation for my Ansible, Dotfiles and Compose Repository, how I did it and why I'm still gonna rewrite everything by hand.**

## Greetings everyone! ##
You heard it right, AI wrote a part of my documentation.
Specifically for my Dotfiles, Compose and Ansible Repo.
But why did I not only allow but also execute this?

Let's find out in this Blog.

### The goal of Februrary.
As you may know, my goal for Februrary was to write documentation for, at this time existing, Repositories.

I come originally from IT Support, so I know just how important documentation is.
That's why I wanted to document exactly what the Code in my Repos do, what you'll need to change and how to use it.

I'm also currently looking into dedicated Wiki or better said Knoledge Base solutions to provide these things even better.
Sadly, I haven't been able to find a solution I like so far, so a dedicated website for that stuff needs to wait.

While time was ticking, I just couldn't bring myself up to to sit there and write documentation for hours after hours.
I already wrote docs for multiple Repos but the ones I mentioned in this blog were by far the biggest ones I had.

I was also pretty busy in this time with other things that needed my attention, may it be other projects or family/friends.

Those things alone consumed much of my time and made me pretty tired in the evening.

### Why I decided to do that? The reasons. ###
Well, there are multiple reasons for that.
In the text above, I already mentioned them real short.

Besides my mood, I just haven't had enough time and energy to write the last few wikis myself.

I'm a man of my word tho, so I knew I need to finish the goal in time.
That's when I realized that I had to throw one promise I made to myself, not using any AI for it, away.

I decided to use Curor, since it has access to my local files.
It could scan them and write documentation accourding to my needs.
The promts looked something like this:
```
Scan the folling files from the current directory, but DO NOT change them in any way:
audiobookshelf/podman-compose.yml
jellyfin/podman-compose.yml
nginx-proxy-manager/podman-compose.yml
semaphore/podman-compose.yml
wordpress/podman-compose.yml
wordpress/env.example
zammad/podman-compose.yml

Then, go into the folder tmp_readme and create markdown files for each projects/folders I gave you.

Name them foldername.md and add instuctions on what the code in it does and how to use it.
They are gonna be wiki pages on codeberg, so make sure the markdown formatting looks good
```

```
perfect, now create a file called Home.md in the tmp_readme directory showing and linking to the correct files.

This is an example of how it should look at the end:
Welcome to the wiki.
Here you can hopefully find answers to the questions you are seeking.
If not, please create an Issue so that I'm getting aware of something missing and be able to add it in the future.
If you already know the answer you can also clone the wiki and create a pr for me to merge!

**Table of content**
- General
    - [Creating service files for systemd](https://codeberg.org/Spoljarevic/Quadlets/wiki/systemd)
- [Steps to setup the wordpress container](link)
    - [Explanation of the compose file](link)
    - [What you need to change in the env. example file before renaming it to .env](link)


Be smart in naming the things and make sure that under link, you have the correct link and link it to the correct file (the files you created but without the .md at the end)
```

As you can see, I wanted it to write structured documentation, but haven't given it much information about what I wanted in it.
Just the information that it's for a wiki was enough for it to write something somewhat okay.

### What exactly did it write? ###
It's easy to see what was written by AI by just looking at the style it wrote it.
It's very generic in the style of writing and presenting it.

Originally, I wanted the text above the table of content in each wiki to be the same.
AI slightly changed that to fit the Repo.

But I have to say, the core message still exists in each and every one of them.
That is, if questions are open, that you either can create an issue or if you already know the answer and just think it's missing, that you can create a pull request to expand the wiki.

But which files are now written by AI?

At the day of writing this, 2026-03-03, these pages are fully written by AI:

#### Ansible ####
```
- **Bash-Scripts to Ansible** (local-only playbooks)
  - [Bash-Scripts to Ansible](Bash-Scripts-to-Ansible)
  - [autostart](autostart)
  - [container](container)
  - [converter](converter)
  - [extractor](extractor)
- **Checks**
  - [checks](checks)
- **Configuration**
  - [configuration](configuration)
  - [hardening](hardening)
- **Deployment**
  - [deployment](deployment)
  - [containers](containers)
  - [wordpress](wordpress)
  - [kubernetes](kubernetes)
- **Health**
  - [health](health)
- **Installation**
  - [installation](installation)
  - [Arch Linux](Arch-Linux)
  - [post-install](post-install)
  - [snippets](snippets)
  - [snippets – installation](snippets-installation)
  - [snippets – random](snippets-random)
  - [snippets – repos](snippets-repos)
  - [developement](developement)
```
**Note that the following is not written by AI:**
```
- **How to use powerfull RHAAP alternatives**
    - [Basics about using Semaphore UI](semaphoreui)
```

#### Compose ####
```
- **Media & streaming**
  - [Audiobookshelf — audiobook and podcast server](audiobookshelf)
  - [Jellyfin — media server (movies, TV, music)](jellyfin)

- **Web & reverse proxy**
  - [Nginx Proxy Manager — reverse proxy and SSL](nginx-proxy-manager)

- **Automation & DevOps**
  - [Semaphore — Ansible UI](semaphore)

- **Web applications**
  - [WordPress — blog/CMS with MariaDB](wordpress)
    - [Explanation of the compose file](wordpress#what-the-compose-file-does)
    - [What to change in env.example before renaming to .env](wordpress#environment-file)
  - [Zammad — helpdesk and ticketing](zammad)
```

#### Dotfiles ####
```
- **Wayland & desktop**
  - [Hypr (Hyprland compositor)](hypr)
  - [Waybar (status bar)](waybar)
  - [Tofi (launcher & powermenu)](tofi)
  - [Dunst (notifications)](dunst)

- **Terminal & shell**
  - [Foot (terminal)](foot)
  - [Kitty (terminal)](kitty)
  - [Zsh (shell config & aliases)](zsh)

- **Applications**
  - [Neovim (TUI based text editor)](Neovim)
  - [lf (file manager)](lf)
  - [ncmpcpp (MPD client)](ncmpcpp)

- **System**
  - [Ly (display manager)](ly)
  - [Cockpit (web admin)](cockpit)
  - [Fastfetch (system info)](fastfetch)
```
**Note that the following is not written by AI:**
```
- [Neovim (TUI based text editor)](Neovim)
```

**Every other page on my other Repos is 100% written by me. No AI used whatsoever.**

### This is only temporary. ###
I want to apologize for using AI in the first place, but don't worry, it won't stay this way.

This is 1. to finish the project but more importantly 2. to have at least some documentation.

As mentioned before, documentation is really important and I didn't want you to figure out what my stuff does.

That's the key reason why I wanted documentation in the first place but also why I won't let it stay like it currently is.

I strongly believe that only a human is capable of writing proper documentation that actually helps people.
When I have more time, I'm gonna go over every single page that Curser AI wrote and to a complete overhaul.

Written by humans, for humans you might say.

This way I can assure that it's written in my style but also that it focuses more of the things that are in my opinion important.
AI can't do that, and probably never will.
Only I can say on what the page needs to focus on.

This is a promise I'm making not only to you, but also to myself.
AI shall never be used again in my documentation and there shall be no trace left of it when I'm done rewriting it.

### Final words ###
This may sound like I'm against AI... I'm not.
Heck, even I use AI for coding sometimes. Or better said for the original structure on what I base my code on.
It is important to always double check what AI gave you and if you can't find a mistake, run a few tests on it.

AI is a bouble that, in it's current phase, will burst sooner or later. But it will never fully go away and we need to accept this.

Use it as a trainee.
Give it simple tasks that you check afterwards, but don't use it like your mentor who you trust without questioning everything it says.

It has a lot of places where it's helpfull, but things like documentation or art ain't one of them.

Be carefull and always question everything it gives you.

**Stay private. Stay root.**
