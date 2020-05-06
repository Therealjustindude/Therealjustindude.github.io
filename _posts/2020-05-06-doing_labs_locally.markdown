---
layout: post
title:      "Doing Labs Locally"
date:       2020-05-06 18:14:16 +0000
permalink:  doing_labs_locally
---


With Covid shaking things up FlatIron has had a lot of new students. New students mearns more demand on the Learn IDE. It is recommended to start doing all labs locally once our local environment is set up. So, I figured I'd show how I get my labs forked and cloned for labs. I hope this helps someone. 

1) While on a lab in learn.co you should see an "OPEN IDE" button, Click on the Github icon located right next to it. If you hover over it you should see "Open In GitHub."

2)Once Github.com is loaded you should see a "Fork" button at the top right. Click that button and it'll copy the lab to your Github repositories. 

3)Click the "Clone or Download" drop down menu. Click the "clipboard" button which will copy the url to your clipboard.

This next part is done in your terminal. You might want to think about where you want to keep your folders and files. I have a folder for FlatIron and folders inside that seperate labs depending on course section. I would recommend learning how to move around your directories inside of terminal as well. 

4)Open your terminal on your computer. It should automatically be at your home directory. To confirm that you should see this ```~```symbol. 

5)Type cd in your terminal(Change directories), space, file path and hit enter ex: ```cd documents/flatiron/sinatra_labs```. The file path depends on where you want to store your labs. 

6) Remember step 3 you saved that url to your clipboard. Now, you are going to use it by pasting it after "git clone" it should look like this in your terminal: 
 ex: ```git clone https://github.com/learn-co-students/sinatra-nested-forms-onl01-seng-pt-021020.git```

You have cloned the lab into your directory.

7)Type cd in your terminal(Change directories), space, the labs folder name and hit enter ex: ```cd sinatra-nested-forms-onl01-seng-pt-021020```

8)Now you're in the lab folder and can type in the command to open your text editor. I am using Visual Studio Code so in my terminal I type ```code .``` and hit enter. This opens the lab files in VSC where you can proceed to work. Don't forget to run ```bundle install```.

I hope this helps. I havent figured out how to add screenshots using the learn blog so I had to be as descriptive as possible. Let me know if something didn't make sense so I can update it. 








