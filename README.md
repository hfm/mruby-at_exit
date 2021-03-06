mruby-at_exit
===

Add `Kernel#at_exit` method in mruby.

```rb
def do_at_exit(str1)
  at_exit { print str1 }
end
at_exit { puts "cruel world" }
do_at_exit("goodbye ")
exit
#=> goodbye cruel world
```

# Installation

On your build_config.rb

```
MRuby::Build.new do |conf|
  # by mgem
  conf.gem :mgem => 'mruby-io-console'
  # by github
  conf.gem :github => 'ksss/mruby-io-console'
end
```

# Implementation

Dependent on `mrb->atexit_stack`.

# Configure

## Call malloc or realloc every time mruby call `at_exit`

Don't define `MRB_FIXED_STATE_ATEXIT_STACK_SIZE` and `MRB_FIXED_STATE_ATEXIT_STACK` in mrbconf.h

## Use static memory

Define `MRB_FIXED_STATE_ATEXIT_STACK_SIZE` and `MRB_FIXED_STATE_ATEXIT_STACK` in mrbconf.h

# Doc

http://docs.ruby-lang.org/en/2.3.0/Kernel.html#method-i-at_exit

# Why doesn't implement to mruby-core?

https://github.com/mruby/mruby/pull/2363
