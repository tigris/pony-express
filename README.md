# Pony Express

A fast and lightweight ruby mailer based on http://github.com/benprew/pony. For a more
historical perspective read [Pony Express](http://en.wikipedia.org/wiki/Pony_Express).

## Installation

```
  sudo apt-get install libmimetic-dev
  sudo apt-get install libpcre3-dev
  sudo gem install pony-express
```

### Dependencies

* Ruby >= 1.9.1
* rubygems >= 1.3.5
* ruby development libraries             (debian: ruby1.9.1-dev)
* mimetic >= 0.9.6 development libraries (debian: libmimetic-dev)
* pcre3 development libraries            (debian: libpcre3-dev)

## Usage

```ruby
  require "pony-express"
  mail = PonyExpress::Mail.new to: "burns@plant.local", from: "homer@home.local", via: "sendmail"
  mail.add cc: "smithers@plant.local", bcc: "carl@plant.local", replyto: "homer+work@home.local"
  mail.add subject: "Hello Mr.Burns", text: "Can I have more donuts ?", html: "<strong>More Dooooonuuuuts!</strong>"
  mail.add attachments: [ "/home/homer/donuts.png" ], headers: [{name: "X-FooBar", value: "test"}]
  mail.dispatch
```

Don't want to create new mail objects ? Just pass in all options to PonyExpress.mail

```ruby
  PonyExpress.mail to: "burns@plant.local", from: "homer@home.local", ...
```

## Testing

```ruby
  require "pony-express"
  require "pony-express/test"
  mail = PonyExpress::Mail.new to: "burns@plant.local", from: "homer@home.local", via: "sendmail"
  mail.add subject: "Hello Mr.Burns", text: "Can I have more donuts ?"
  mail.dispatch
  assert_equal 1, PonyExpress::Test.mailbox.length
```

## TODO

* Build a rainbow machine and rope in some unicorns.

## Won't Do

* Support for Ruby 1.8 or Rubinius or JRuby
* MIME parsing. If you need a full blown mail library have a look at the mail gem.

## License

GNU GPLv3, so its free and comes with no guarantees. If it brings down your website or burns down your house, I will
not be held responsible. Use it at your own risk. You can read all about GNU here: http://www.gnu.org and
GNU GPLv3 here: http://www.gnu.org/licenses/gpl.txt.
