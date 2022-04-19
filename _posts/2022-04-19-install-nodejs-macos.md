---
layout: post
title: Install Node.js on MacOS
excerpt_separator: <!--more-->
---

Node.js is an open source development platform for executing JavaScript code server-side. While JavaScript runs natively in a browser (i.e. client-side), Node.js provides developers the platform with which to build applications for a controlled environment that runs on a host computer, separate from the JavaScript that is delivered to the client's browser. In this way, a Node.js application is comparable to PHP, Java, and Ruby, and other application environments that handle web-traffic requests, but are not delivered to the client.

To develop a Node.js application on MacOS, the Node binaries must be installed.

<!--more-->

### 1. Create a user with admin access.
Chances are you are already a user with admin access. If you are aware that you are not a user with admin access, follow [these steps](https://osxdaily.com/2017/07/17/how-create-new-admin-account-mac/) (osxdaily.com) to create such a user. You will need a user *with* admin access to create this new user.

<div class="spacer"></div>

### 2. Install Homebrew
```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew -v
```

<div class="spacer"></div>

### 3. Remove existing node versions
```
$ brew uninstall --force node
```

<div class="spacer"></div>

### 4. Install NVM
```
$ brew update
$ brew install nvm
```

<div class="spacer"></div>

### 5. Follow the instructions output by the nvm installer
```
You should create NVM's working directory if it doesn't exist:

  mkdir ~/.nvm

Add the following to ~/.zshrc or your desired shell
configuration file:

  export NVM_DIR="$HOME/.nvm"
  [ -s "/usr/local/opt/nvm/nvm.sh" ] && \. "/usr/local/opt/nvm/nvm.sh"  # This loads nvm
  [ -s "/usr/local/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/usr/local/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion

You can set $NVM_DIR to any location, but leaving it unchanged from
/usr/local/opt/nvm will destroy any nvm-installed Node installations
upon upgrade/reinstall.

Type `nvm help` for further information.
```

Practically, issue the following commands
```
$ mkdir ~/.nvm
$ nano ~/.zshrc
```

Copy and paste the script from the output within `.zshrc`, and use the command `source` to load the new configuration into the active terminal.

```
$ source ~/.zshrc
```

<div class="spacer"></div>

### 6. Install the latest long-term support version of Node.js.
```
$ nvm install --lts
$ nvm current
```

`nvm current` displays the currently active node version. It should be the version that was installed with `nvm install --lts`.

<div class="spacer"></div>

### 7. Check the installations
You should now have nvm and Node.js installed. Check the installation. Here are the commands with example output.
```
$ nvm -v
0.39.1
$ node -v
v16.14.2
```

Now that Node is installed, get to building out your application. Check out the sample web-server [provided by the Node.js team](https://nodejs.org/en/docs/guides/getting-started-guide/). But listen! Node.js is useful for more than serving web requests. Node.js can be used to build desktop applications, command-line scripts, and developer libraries (things that can be `npm install`ed).

---

## Resources

Similar walkthrough: https://tecadmin.net/install-nvm-macos-with-homebrew/