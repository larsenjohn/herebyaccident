---
layout: post
title: Global .gitignore
---

# Global .gitignore

Some smartypants said I have been serving up .DS_Store files all over the interweb tubes. Well, I guess it was McAffee, so there is no accounting for how crazy this advice is. It's sort of like Gary Busy giving you pointers. However, these files are the herpes of OSX.

***
<hr class="rule">

Make a new .gitignore file.

<pre>
sudo nano ~/.gitignore_global
</pre>

.gitignore_global

<pre>
#compiled source #
###################
*.com
*.class
*.dll
*.exe
*.o
*.so

# Packages #
############
# it's better to unpack these files and commit the raw source
# git has its own built in compression methods
*.7z
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip

# Logs and databases #
######################
*.log
*.sql
*.sqlite

# OS generated files #
######################
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db

# codekit #
###########
.sass-cache/
.codekit-config.json
config.codekit
</pre>

Assign it.

<pre>
git config --global core.excludesfile '~/.gitignore_global'
</pre>

Check config if you get nervous.

<pre>
git config --list
</pre>
