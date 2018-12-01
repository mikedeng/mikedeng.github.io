---
layout: post
title:  "Node 和 rails 环境安装"
date:   2016-11-03 22:30:39

categories: server
---


```bash
sudo ap-get update

# 1. git
sudo apt-get install git  -y
sudo apt-get install gitg -y
sudo apt-get install tig  -y
sudo apt-get install vim  -y
sudo apt-get install mysql-server-5.5 -y
sudo apt-get install -fy
sudo apt-get install openjdk-7-jdk -y

# 2. oh-my-zsh
sudo apt-get install curl -y
sudo apt-get install wget -y
sudo apt-get install zsh  -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
source ~/.zshrc


# 3. rbenv, depends(git)
git  clone git://github.com/sstephenson/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.profile
echo 'eval "$(rbenv init -)"' >> ~/.profile
git  clone git://github.com/sstephenson/ruby-build.git  ~/.rbenv/plugins/ruby-build
source ~/.zshrc

# 4. alias apt
echo "alias apt='sudo apt-get install'" >> ~/.zshrc


# 5. solve the passenger with nginx installation error
sudo apt-get install libcurl4-openssl-dev -y

# 6. node & npm
curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash - && apt nodejs
apt  nodejs -y
apt  npm    -y
sudo npm    install npm@latest -g

# 7. ruby
apt   libssl-dev libreadline-dev zlib1g-dev  -y
rbenv install 2.3.1
rbenv global  2.3.1
gem   sources --remove https://rubygems.org/
gem   sources --add https://gems.ruby-china.org/
rbenv rehash
source ~/.zshrc

# 8. rails
gem   install rails -v 5
rbenv rehash

# 9. passenger
gem install passenger
rbenv rehash

# 10. bundler
gem install bundler
rbenv rehash

# 11. chrome
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
rm  -rf google-chrome-stable_current_amd64.deb

# 12. sublime text 3.12.6
wget 'https://download.sublimetext.com/sublime-text_build-3126_amd64.deb'
sudo dpkg -i sublime-text_build-3126_amd64.deb
rm   -rf sublime-text_build-3126_amd64.deb

# 13. nginx should install in the last
sudo `which passenger-install-nginx-module`
# start: `sudo /opt/nginx/sbin/nginx`,  
# shut:  `ps auxw | grep nginx`
# kill process  `sudo kill $(cat /opt/nginx/logs/nginx.pid)`

# 14. add nginx to the init.d
sudo cp ./nginx /etc/init.d/nginx
sudo chmod +x /etc/init.d/nginx
sudo /usr/sbin/update-rc.d -f nginx defaults
sudo service nginx start


##################################################################### nginx
#! /bin/sh

### BEGIN INIT INFO
# Provides:          nginx
# Required-Start:    $all
# Required-Stop:     $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: starts the nginx web server
# Description:       starts nginx using start-stop-daemon
### END INIT INFO

PATH=/opt/nginx/sbin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/opt/nginx/sbin/nginx
NAME=nginx
DESC=nginx

test -x $DAEMON || exit 0

# Include nginx defaults if available
if [ -f /etc/default/nginx ] ; then
        . /etc/default/nginx
fi

set -e

case "$1" in
  start)
        echo -n "Starting $DESC: "
        start-stop-daemon --start --quiet --pidfile /opt/nginx/logs/$NAME.pid \
                --exec $DAEMON -- $DAEMON_OPTS
        echo "$NAME."
        ;;
  stop)
        echo -n "Stopping $DESC: "
        start-stop-daemon --stop --quiet --pidfile /opt/nginx/logs/$NAME.pid \
                --exec $DAEMON
        echo "$NAME."
        ;;
  restart|force-reload)
        echo -n "Restarting $DESC: "
        start-stop-daemon --stop --quiet --pidfile \
                /opt/nginx/logs/$NAME.pid --exec $DAEMON
        sleep 1
        start-stop-daemon --start --quiet --pidfile \
                /opt/nginx/logs/$NAME.pid --exec $DAEMON -- $DAEMON_OPTS
        echo "$NAME."
        ;;
  reload)
          echo -n "Reloading $DESC configuration: "
          start-stop-daemon --stop --signal HUP --quiet --pidfile     /opt/nginx/logs/$NAME.pid \
              --exec $DAEMON
          echo "$NAME."
          ;;
      *)
            N=/etc/init.d/$NAME
            echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
            exit 1
            ;;
    esac

    exit 0

```