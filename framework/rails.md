#


##

https://ruby.taobao.org/
https://gems.ruby-china.org/

Change gem source:

    $ gem update --system
    $ gem -v
    $ gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
    $ gem sources

For Gemfile and Bundler:

    $ bundle config mirror.https://rubygems.org https://gems.ruby-china.org

