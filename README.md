## Yet Another Rubygems Proxy

> Yarp is a small [Sinatra](http://www.sinatrarb.com) app that makes your [bundler](http://bundler.io) faster.
> You'll love it if you deploy a lot.

On a medium-size application with 34 direct gems dependencies, running `bundle install` takes me:

- Without Yarp: 18.5 seconds
- With Yarp: 10.0 seconds

Thats a 45% percent win right there. 8 seconds shaved of my deploy times.
If you deploy 20 times a day to your staging environments and 5 times a day to production, you're getting 15 minutes of your life back every week. Make those count!


### Installation and usage

Deploy your own Yarp or use the one at `yarp.io`.

Just replace this line on top of your Gemfile:

    source 'http://rubygems.org'

By this one:

    source 'http://us.yarp.io'

Or if you're in Europe:

    source 'http://eu.yarp.io'


### How it works & Caveats

Yarp caches calls to Rubygem's dependency API, for 24 hours if using `yarp.io`. It redirects all other calls to Rubygems directly.

This means that when gems get released or updated, you'll lag a day behind.

It also means that _downloading_ the gems themselves is not sped up—they're cached in Rubygem's CDN anyways.


### Running locally

Checkout, make sure you have a [Memcache]() running, configure `.env`, and

    $ bundle exec foreman run rackup

When developping (by default) cache expires after 1 minute.


### License

Yarp is released under the MIT licence.
Copyright (c) 2013 HouseTrip Ltd.