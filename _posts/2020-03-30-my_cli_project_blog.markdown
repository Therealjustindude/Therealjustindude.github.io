---
layout: post
title:      "My CLI project Blog "
date:       2020-03-30 17:42:24 -0400
permalink:  my_cli_project_blog
---



My project displays a list of tequila drinks to a user. When a user selects a drink they are presented with a shopping list. They have the option to see the list of drinks again or see the instructions on how to make that drink. I wanted to make an application that lists tequila drink because I believe >“If you want to make some memories, add some tequila." 

Let me talk about some hiccups. I knew I had to make two API calls. the first would get  the drink name and drink ID. The second call would use the drink ID to collect the attributes of each drink. I only wanted my TequilaDrink class to have the attributes name, drinkID, instructions and ingredients. My initial thoughts were, my CLI class would need to ask for a user to select a drink so I could use that drinks ID to search my API for the attributes. My thought process was, if I don’t know what drink the user is selecting how will my API know what drink ID to use and collect attributes from. With that, I thought my CLI class should be collecting attributes from my API class so I could use those attributes to create TequilaDrink objects. I spent a lot of time on this first hiccup. It took a meeting with my instructor for the light bulb to turn on. I switched my focus to having my API class instantiate new objects in my TequilaDrink class so those attributes can be accessed by my CLI class. After I refocused I was able to set the attributes I wanted for the tequila drink objects.

The next hiccup was figuring out how my CLI class will handle invalid entry and take my user through their options. To start, I focused on taking my user through the program if they followed the rules and do not misspell anything. It wasn’t easy and it looked messy. I had conditionals in my #welcome_message method that could’ve been put inside separate methods. It felt sloppy. When a user got through a cycle of picking a drink, receiving the shopping list and reading the instructions my application would ask if they’d like to see the list again or exit. If they choose the list the welcome message would print and the list would be displayed again. So, I created a new #start_and_list_drinks method. I wanted a user to ask for the list again and just see the list. The only time they need to see the welcome message is when they start my application. With that out of the way I started on handling invalid entries. 

I understood that every time I got user input I needed to validate that input. Knowing that I decided to code methods that would have if-else conditionals able to test the input. I also created a #invalid_entry method. With the methods to test input and the #invalid_entry method a user is able to navigate around my application. It was functioning how I imagined it. 

This was my first project and it has challenged me like I have never been challenged before. I had doubts. There were some weak moments. But, I am proud to say I got through it. The challenges I solved on my own felt amazing. I can’t say I’ve felt that kind of excitement. I felt smart and mentally strong. I’m looking forward to what is next.

