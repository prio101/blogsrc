---
layout: post
title:  "Getting up  with RVM"
date:   2015-01-18 13:25:05
author: Mahabub Islam
categories: technology Ruby RVM
image: true
---

There is many times in different blogs and in forums I watch a post about *ruby installtion problem* . Even if I stay honest I also face that kind of problem . People love *Ruby* and it's framework [Rails](http://rubyonrails.org/)because it is easy and powerfull. But when it is not managed it can become very complex.

{% if page.image %}
 <div class="post-img">
 <img class="img-responsive img-post" src=" {{site.baseurl}}/img/ruby.png "/>
 </div>
{% endif %}

You see while developing with Ruby On Rails , there is typical time that you are dealing with the different versions of ruby installtion. So , today I am going to talk about that kind of tool which will manage Ruby installation for you. This post will pretty short and follow along you will like what you have learnt.

** What is RVM? ** It is like a box which holds all the ruby installation and while development you only have to choose which version to work with. It holds all the gem nedded in aspecific ruby installation and never mess up the another ruby instllation.

**How to Get it** Well here I come with the steps you need to follow to get the [RVM](https://rvm.io/).

##### Step 1:  

I hope you are using UBUNTU or any Linux based system , so please type ```ctrl```+```alt```+```t``` which will bring up your Terminal . After that type ,

	$ gpg --keyserver hkp://keys.gnupg.net --recv-keys D39DC0E3

After hitting the ```Enter``` key This command will grab some data and bind it for greater good.			  

##### Step 2:

So now in this step just write some more text in your terminal ,which will install the *RVM*,

	$ \curl -sSL https://get.rvm.io | bash -s stable

This will install the **Stable** version of *RVM* in your computer, but if your terminal shows some error about not finding the **Curl** package then don't be scared . You can get it by Typing,

	$ sudo apt-get install curl

After the installtion of curl you can always install *RVM* by writing previous line.

##### Step 3:
Now take a deep breath and go in your Terminals ```Edit```-> ```Preference``` menu and check the *Run terminal as login shell* option . Restart the Terminal. And its done.

##### Step 4:
So now in your terminal you can check for all the available Ruby out there , by typing,

	$ rvm list known

Which will show the ruby package ready to get hop in your computer . To install them type,

	$ rvm install 2.1 # Or any version you do prefer

This command will install the *Ruby* in your machine . You can recheck your installtion and see which one is currently using by typing ,

	$ rvm list

---
After getting this awesome tool , you can also look into the **RBENV** which is almost like **RVM** . And as from my view rather complex one out there. You can get all the documentaion in [RVM DOCS](https://rvm.io/) and if you ran into some problem , you always can ask. Until next time , take care. 	




