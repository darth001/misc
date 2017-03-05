# Ruby

https://www.ruby-lang.org/
http://rvm.io/
https://ruby.taobao.org/

## source code

    $ wget https://cache.ruby-lang.org/pub/ruby/2.2/ruby-2.2.6.tar.gz
    $ tar xf ruby-2.2.6.tar.gz
    $ cd ruby-2.2.6
    $ ./configure --prefix=/usr/local/ruby
    $ make
    $ sudo make install

## dnf

    $ sudo dnf -y install ruby ruby-devel

## rvm

    $ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
    $ curl -sSL https://get.rvm.io | bash -s stable

## RubyGems mirrors

    $ gem sources --list
    $ gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
    $ gem install rails jekyll

    $ bundle config mirror.https://rubygems.org https://gems.ruby-china.org
