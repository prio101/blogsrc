---
layout: post
title:  "Power of jekyll"
date:   2015-01-17 23:25:05
author: Mahabub Islam
categories: technology jekyll static site-generator
image: true
---



There is some powerful tools out there in the big vast ocean of the technology.
Some of them is like ,  very  generous  toward the needs
of a very specific task and thus they never get lost or never lost their charm.

{% if page.image %}
 <div class="post-img">
 <img class="img-responsive img-post" src=" {{site.baseurl}}/img/jekyll.png "/>
 </div>
{% endif %}

Well If I stop being poetic and little bit dramatic then , I would say [Jekyll](http://jekyllrb.com/)
is a kind of that technology .

You can ask , why so being dramatic about that thing , The answer is very short
It is task oriented. If you are someone who want to run a **Blog** or **Static-Site** and really do
not want to take the hustle of Database management  stuff.
*Jekyll* is ready for you to pick up.

A little intro of Jekyll ? not many history. Jekyll is a **Ruby Gem** and by saying it I want say
you can install it in your computer just by writing one command ,
which is,

		
	
	  $ gem install jekyll
			

And all of a sudden you are ready to run **Jekyll**.

I am going to demonstrate all the step you need to run jekyll in your computer

I hope like me you are also running an [Ubuntu](http://ubuntu.com) based computer.

so the prerequisites are ,

1 . Ruby installed in your computer [ I prefer you install it with RVM ](http://rvm.io/)
    or , you simply can install it with **apt-get** package manager.
    with this command, open your *Terminal* and write,

  	
      $ sudo apt-get install ruby
  	
   
   And this will come with latest stable package of Ruby available for your PC with
   *gem* installer packed.

2 . You will have to install nodeJs in your computer which is like new pie of Developing world.
For this I suppose you will have to have CURL installed in your PC . which is mendatory for a
developer.
steps:

    
       $ sudo apt-get install curl

I am encoraging you to follow along the steps in [Github](https://github.com/joyent/node/wiki/installing-node.js-via-package-manager)

But , meantime you can install it in ubuntu by
	
      $ curl -sL https://deb.nodesource.com/setup | sudo bash -

      $ sudo apt-get install -y nodejs
    	
    
    
Easy , right?

3 . After these installation you can check is it in there (Which is really is)
   by typing:

   [If installed the ruby package]
    
    	
	
      $ ruby --version
   
    

   [If using RVM]
   
	
	 $ rvm list
   	

   [For NodeJs]
   
   	
      $ node --version
   


4 . So now everything you need is ready , its time to install the **jekyll** ,  let's do it by ,
	
	  $ gem install jekyll 
   	
   And this will install all the jekyll stuff automatically.

5 . Now you are ready ; after some few commands and having some powerful **Coffee** .
   Just get to a directory where you will like to have your jekyll up and running

   If confused , then follow these steps,


   
      $ cd  			# This will take you to the HOME folder

      $ mkdir test  		# This will make you a folder named test

      $ cd test  			# This will cahnge  your directory to test 

      $ jekyll new site		# This will yes make new jekyll site 

      $ cd site			# This change your directory in site folder

      $ jekyll serve		# Well this will serve you a freshly cooked jekyll
   

   <h3> Bam!!! you are awesome</h3>

   by this time you can see your **Terminal** is showing some handful of commands executing in course of generating
   your first **Jekyll** site.

   And if you can't wait to see how it really look like , then happily go to your web browser and write down *localhost:4000* in your address bar.
   And its ready there to welcome you with fresh installation.


### Advantages:
 * No database hastle.
 * You can write in [Markdown](http://en.wikipedia.org/wiki/Markdown) format.
 * You can host your site in [GITHUB](https://github.com) for free.
 * You will have a great documentation in [Jekyll Docs](http://jekyllrb.com/docs/home/) site.
 * Even this site is running in Jekyll with Free hosting from Gitub like many other site in this [List](https://github.com/jekyll/jekyll/wiki/sites)

So , folks I hope you people are willing give it a try. And in the mean Time you can leave your comment below. I will try to answer any qusetion or stuff you need to know.

Hope to write more in this blog. until then take care. 
