# Installation

You will need to install from CPAN at least the following packages:

 * Bot::BasicBot
 * File::pushd
 * XML::RAI, XML::RPC, and XML::SAX
 * Module::Pluggable
 * MooseX::NonMoose
 * POE::Component::SSLify (if you want to connect with SSL)

# Configuration

The repo is configured by default for running a development version of the
official Cheibriados bot. To change this:

 * Edit the channel names and nick in `bin/run`.
 * Edit the admin user names in `lib/Crawl/Bot/Plugin/Puppet.pm`.
 * If you're running something completely different from Cheibriados, you may
   want to edit the channel names in `lib/Crawl/Bot/Bot.pm` `around say`, which
   keep a development version from duplicating an official version in the
   channels specified there.

To enable SSL on the bot's connection, make sure you choose the correct port,
and add `ssl => 1` to the list of properties in `bin/run`. For example:

    Crawl::Bot->new(
        server   => 'irc.libera.chat',
        port     => 6697,
        ssl      => 1,
        channels => ['#crawl-dev'],
        nick     => 'FakeCheibriados',
        name     => 'FakeCheibriados the Crawl Bot',
    )->run;

To use nickserv, put the password in plaintext in a file called `.password` in
the root directory of the repository. Needless to say, this is not a secure
way of storing passwords.

# Running

From the root directory of the repository, call `bin/run`.
