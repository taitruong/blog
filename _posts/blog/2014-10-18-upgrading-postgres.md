---
layout: post
title: "Upgrading from Postgres 9.2 to 9.3 on Heroku"
categories: blog
excerpt: "Why I stoped loving and started hating PaaS"
tags: [development]
author: hlgr360
share: true
---

It is no secret that we build [launchd.de](http://wwww.launchd.de) using Ruby on Rails and are running it on Heroku. It was the fastest and easiest way to get the platform up and running one year ago. But while the experience of using Ruby on Rails has been nothing short of transformative, my experience with Heroku has been a decidedly mixed bag.

From the looks of it a Platform-as-a-Service (PaaS) is just brilliant. It takes away all the pain of managing your deployment on an Infrastructure-as-a-Service (IaaS) while preserving the inherent scalability. And Heroku makes on-boarding super easy. Literally signing up and a 'git push' and you are on your way. But baked into a PaaS are certain mental models and assumptions about how your app is suppose to be like. Maybe call it best practices, but in the end it might just be that **"my best practices are your worst nightmares"**. Our first rookie mistake cost us 2 weeks in launching [launchd.de](http://wwww.launchd.de). We had simply forgotten to fix the version numbers in our Gemfile. And since half a year had passed from starting to code to actual launching, the initial deploy to Heroku resulted in countless gem upgrades which ultimately broke our app. Fine - lesson learnt (since we have day jobs to attend to, the resulting forklift upgrade cost us 2 weeks.). Then - a couple of months later - came a system wide upgrade of Rails (or was it Ruby) which cost us another week or so. And so on and so on.

Remember, the initial promise of a PaaS was that we did not have to worry about the infrastructure  - yet the reality of running a SaaS platform on a PaaS is that you still need to care, just at a higher level. True, I don't need to provision machine instances and load balancers, but now I need to worry about forklift upgrades of frameworks I am relying on (which force me to deal with version incompatibilities of something which worked previously when I should be focussing on new features for my customers). This does not even mention problems with the Rails asset pipeline apparently working differently on my local dev system vs in Heroku.

What motivated me to this column was the latest episode of such an upgrade. We had exceeded the free database tier and were forced to upgrade to the first paid tier. Except that the free tier was Postgres 9.2 and the paid tier was Postgres 9.3. I need to add that we have wrapped our deployment process in a script which backs up our customer database both via the 'pgbackup' plugin of Heroku and to local file. After pushing the latest version of our code repo we would reset the database and restore from backup. This allows us to extend existing database schemas "in place" rather than keep adding consecutive migration files (I really dislike a directory with lots - and I mean lots - of files). Unfortunately the pg_dump for PG 9.2 will not work with a PG 9.3 instance - so for all sense and purpose our deployment process was broken after we switched to the paid tier. And sure - you could argue that it was our choice to structure our deployment process in this way, but guess what - this is exactly what I mean by "every PaaS has certain practices and mental models built in". You follow them - your are fine. You break them knowingly or unknowingly - you are in for a lot of pain (and guess what, most of the baked-in assumptions are not even documented anywhere). To tie it back to my day job - PaaS are like [API SDK's - they work until they don't](https://hlgr360.github.io/blog/blog/sdks-work-until-they-dont/).

But fair enough - with a university wanting to use our platform for their entrepreneur course and certain features and bug fixes I needed to get in before the deadline, I had to upgrade my local environment from Postgres 9.2 to 9.3. I did not want to risk a single byte of data of my customers and was not willing to drop the ability to create a backup of the data locally.

As you can imagine (why would I write this blog otherwise), the upgrade itself turned a bit into a nightmare. Even though it was suppose to be the most simple of all - I had no data locally to preserve - simply dropping PG 9.2 and installing PG 9.3 should have been sufficient. Except I struggled to get PG 9.3. to work with my local Rails installs for a couple of long nights (remember, I have a day job). So if you think you did everything right upgrading to PG 9.3 but encounter the following problem

```text
could not connect to server: No such file or directory
Is the server running locally and accepting connections on Unix domain socket
"/var/run/postgresql/.s.PGSQL.5432"?
```

I can hopefully save you a few hours by pointing out that PG 9.3 appears to have changed its default port from 5432 to 5433. The corresponding configuration file

```text
/etc/postgresql/9.3/main/postgresql.conf

#------------------------------------------------------------------------------
# CONNECTIONS AND AUTHENTICATION
#------------------------------------------------------------------------------

# - Connection Settings -

listen_addresses = 'localhost' # what IP address(es) to listen on;
# comma-separated list of addresses;
# defaults to 'localhost'; use '*' for all
# (change requires restart)
port = 5433 # (change requires restart)
max_connections = 100 # (change requires restart)
```

The TCP port shows up as part of the UNIX domain socket filename. So if your Postgres instance is listening on 5433 but your Rails app is expecting it on 5432 (Rails will default to 5432 if you do not specify Port in "config/database.yml") you will get above error. I ended up adding both the Port directive to my database.yml file and configuring Postgres to listen to port 5432. This - btw - also allowed phpPgAdmin to connect to the database again since it was also implicitly defaulting to port 5432 (it had shown a 'Login Invalid' error when it could not connect).

Here are the links which helped me to get a working Postgres 9.3 instance up and running:

* http://stackoverflow.com/questions/10263821/rails-rake-dbcreateall-fails-to-connect-to-postgresql-database
* http://www.unixmen.com/install-postgresql-9-3-phppgadmin-centos-6-5/

So what are my conclusion? Well - I am already knee deep into moving our platform into Docker, well [Vagrant](http://www.vagrantup.com/downloads.html) + [CoreOS](https://coreos.com/docs/running-coreos/platforms/vagrant/#single-machine) + [Docker](http://www.talkingquickly.co.uk/2014/06/rails-development-environment-with-vagrant-and-docker/) to be precise. First with our development setup and then onto Amazon for production. Ultimately **control over my runtime environment in an IaaS trumps the backloaded convenience of a PaaS**. I will keep you posted.