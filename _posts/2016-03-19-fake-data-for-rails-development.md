---
layout: post
title:  "Fake Data For Rails Development"
date:   2016-03-19 22:25:05
author: Mahabub Islam
categories: technology rails tutorial faker gem
image: true
---

While developing web-application we always face such circumstances , when we are in badly need of some real-looking data which can get our application features in a proving position , for showing it to our client or even team or sometime it is highly recommended to create fake data that we can test against it the features we have created.

Ruby On Rails framework which is made upon Ruby-Language provide a easiest backed way that we can add seed data or fake data . But this process is also tedious .

But there are some more ways to do this in convenient way , Thanks to Community of Ruby On Rails that they provide us many options .

Faker is one of them which is also easy to use.

Well , let me show a quick bake recipe for you all. You can download this Gem in your rails application with,

    gem install faker

More help are available on [installation](https://rubygems.org/gems/faker)

Basic Usage: Example of usage would be like:

    Faker::Name.name      #=> "Christophe Bartell"

    Faker::Internet.email #=> "kirsten.greenholt@corkeryfisher.info"

    Faker::Color.hex_color #=> "#31a785"

    Faker::Color.color_name #=> "yellow"

    Faker::Lorem.sentence #=> "Dolore illum animi et neque         accusantium."

    Faker::Lorem.sentence(3) #=> "Commodi qui minus deserunt sed vero quia."

You can always make awesome application by harnessing power of faker and all the other gems Community prepared for you and continuously developing for you.

Because why not , You are human , and you develop human friendly application.