Install a Package Manager
===============

- First install brew 

  <pre><code>
    % ruby -e "$(curl -fsS http://gist.github.com/raw/323731/install_homebrew.rb)"
    % brew search
    % brew install jdk
    % brew uninstall jdk
  </code></pre>
  
  Note that there are other options to brew -  macports and fink.
  Brew is the simplest to install and use, but it tries to reuse existing 
  libraries on OSX. This makes it faster and simpler, but it may also break
  when your OSX version does not have the latest libraries (esp. for tools
  that have Xcode dependencies). 
  
  Macports is the next best bet - it tries to build from source, and can
  get the dependent library-sources as well. However it can break in confusing ways.
  Fink is based on apt-get gets binaries, but tends to be out-of-date.

  See http://tedwise.com/2010/08/28/homebrew-vs-macports/ for a comparison.


Directory Setup
===============

  <pre><code>
  shamik
    .ssh/           :  put id_rsa  and id_rsa.pub 
    .ec2/           :  see ec2-setup.txt 
    bin/            :  put all scripts here  ( from basesetup/bin )
    sdk/            :  jdk, flex_sdk, ruby, python, 
    tools/          :  tornado
    work/           :  professional work related projects
    proj/           :  personal projects
    proj/macsetup/  :  get macsetup from github
  </code></pre>
  

Install important  libraries, tools
=============

Install a bunch of tools
<pre><code>
    % brew install wget
    % brew install git
    % brew install virtualenv
    % brew install jdk 
</code></pre>
 
- Create a  Virtualenv 
<pre><code>
    % cd ~/proj
    % virtualenv --no-site-packages --distribute --python=/usr/local/bin/python venv
    % source venv/bin/activate
</code></pre>

- Flash SDK  
   Also install flex_sdk_debug from Adobe.
   Note that using DEBUG flash player on Chrome is harder because Chrome has a built-in Flash
   (nondebug) player that it defaults to. You can go into Chrome settings and point it to the
   debug player if you wish.

- MySQL


Applications (free)
===============
* Firefox
* Chrome
* Picasa
* Skype
* Dropbox
* Evernote
* iTerm
* ImageMagick
* Sequel Pro  (or MySQLWorkbench)
* Tunnelblick

Applications (Paid)
===============
* Keynote
* Parallels/VirtualBox + Windows 
* Fireworks
* SublimeText / TextMate 
* Adobe Flash Builder
* Lightroom ($249)
* Tower for git control
* Flash Decompiler Trillix
* Tableau Desktop (on Parallels/Windows) for BI
* Zooom2 and Sizeup (configured for cntl-option-command  with arrow keys)

Services
===============
* Github
* TargetProcess / Pivotal / Accunote
* NewRelic



Setup bash
===============
    
<pre><code>
    % vi .bash_profile 
     export HOME= /Users/shamik
     export PS1="\u@\w>"
     export PATH=$HOME/bin:$PATH
     export PATH=$PATH:/usr/local/git/bin:$HOME/tools/flex_sdk_4/bin
     export PYTHONPATH=$HOME/lib/tornado 
</code></pre>




Setup Aliases and handy bin/ scripts
===============

* SSH Mysql tunnels

<pre><code>

  Create the tunnel (localhost:3308  tunnels to  db.server.com:3306)
  % ssh -fNg -L 3308:127.0.0.1:3306 root@stage-db-02.server.com -i ~/.ec2/my_aws

  Test it :
  % telnet localhost 3308   # OR
  % nc -v localhost 3308    # netcat is basically a telnet

  Kill it
  % lsof -i :3308   # When done, find the process using the port and kill it.

</code></pre>
