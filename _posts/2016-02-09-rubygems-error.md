---
layout: post
title: "RubyGems Error"
date: 2016-02-09 19:30:00
tags: ruby rubygems
---

While trying to get some environment variables setup with Travis CI using the travis gem from the command line I ran in to this error:

~~~ bash
$ travis encrypt SPOTIFY_CLIENT_ID=<obfuscated>
/Users/Cameron/.rvm/rubies/ruby-2.3.0/lib/ruby/site_ruby/2.3.0/rubygems/specification.rb:2159:in `method_missing': undefined method `this' for #<Gem::Specification:0x3ff7a8d716f0 travis-1.8.2> (NoMethodError)
        from /Users/Cameron/.rvm/rubies/ruby-2.3.0/lib/ruby/site_ruby/2.3.0/rubygems/specification.rb:1057:in `find_active_stub_by_path'
        from /Users/Cameron/.rvm/rubies/ruby-2.3.0/lib/ruby/site_ruby/2.3.0/rubygems/core_ext/kernel_require.rb:64:in `require'
        from /Users/Cameron/.rvm/gems/ruby-2.3.0/gems/travis-1.8.2/lib/travis/cli.rb:2:in `<top (required)>'
        from /Users/Cameron/.rvm/rubies/ruby-2.3.0/lib/ruby/site_ruby/2.3.0/rubygems/core_ext/kernel_require.rb:127:in `require'
        from /Users/Cameron/.rvm/rubies/ruby-2.3.0/lib/ruby/site_ruby/2.3.0/rubygems/core_ext/kernel_require.rb:127:in `rescue in require'
        from /Users/Cameron/.rvm/rubies/ruby-2.3.0/lib/ruby/site_ruby/2.3.0/rubygems/core_ext/kernel_require.rb:40:in `require'
        from /Users/Cameron/.rvm/gems/ruby-2.3.0/gems/travis-1.8.2/bin/travis:7:in `<top (required)>'
        from /Users/Cameron/.rvm/gems/ruby-2.3.0/bin/travis:22:in `load'
        from /Users/Cameron/.rvm/gems/ruby-2.3.0/bin/travis:22:in `<main>'
        from /Users/Cameron/.rvm/gems/ruby-2.3.0/bin/ruby_executable_hooks:15:in `eval'
        from /Users/Cameron/.rvm/gems/ruby-2.3.0/bin/ruby_executable_hooks:15:in `<main>'
~~~

After a bit of googling, this got it working:

~~~ bash
gem pristine --all
~~~

Cheers!
