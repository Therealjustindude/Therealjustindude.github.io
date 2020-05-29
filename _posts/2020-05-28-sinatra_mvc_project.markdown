---
layout: post
title:      "Sinatra MVC Project"
date:       2020-05-29 03:21:42 +0000
permalink:  sinatra_mvc_project
---

When I first thought about learning to code I came across HTML and CSS. I bought a course but didn’t take to it well. At the time, I remember thinking how do these HTML, CSS and javascript files turn into web applications that people can visit and use. Everything I learned in the Sinatra section at Flat Iron is showing me how websites are made. I am enjoying this because I am learning that there are so many ways to get it done. I’m finding it important to be adaptable. 

My project is called Habitual Habits at the moment a user can sign up or log in, view, add, update and delete habits. A user can not edit a habit if they don’t have association with that habit. I used gems like ‘corneal’ to lay the blueprint for my project, ‘bcrypt’ to encrypt a users password in the database, ‘dotenv’ and ‘sysrandom’ to store an encrypted session password in an environment variable and ‘sinatra-flash’ to display flash messages to inform a user why the website isn’t doing what they want. 

I had a lot of fun figuring out all the problems I came across and figuring out some CSS to make my project look nice. The issue I spent the most time on was in the post route. A user can pick from a list of habits or create a new one. What I was having trouble because a user was able to add the same habit over and over. Also, I needed to figure out how to use the information based on whether a user picked from the list or entered a new habit not on the list. I created a helper method in my user model to check a users habit association:

``` def associated_habit?(habit)
       self.habits.include?(habit)
   end ```
	 
and a few conditionals in my post route:

``` verify_user_logged_in
       
        found_habit= Habit.find_by_id(params[:habit_id])
        
        @current_user.habits << found_habit if found_habit && !(@current_user.associated_habit?(found_habit))
        
        new_habit = Habit.new(habit: params[:habit].downcase) if params[:habit].present?
        
        if new_habit && new_habit.save
            @current_user.habits << new_habit if !(@current_user.associated_habit?(new_habit))
        end
        
        redirect "/habits" ```


This project was fun and I look forward to my next one using rails.
