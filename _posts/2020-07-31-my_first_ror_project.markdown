---
layout: post
title:      "My first RoR Project"
date:       2020-07-31 23:19:20 +0000
permalink:  my_first_ror_project
---


	Let me start by saying, this was a fun project. My mind was blown by some gems. I had some really good pair programming sessions. I got really close with binding.pry. And I learned some cool CSS. What I want to do for my blog is answer questions to help me prepare for an assessment.

How do we represent relationships between models in our tables?

	I represent relationships between models in my tables with foreign keys. A Dog belongs to a User so the user_id would be kept in the dogs table. This will help keep track of what dog belongs to a particular user. A journal entry belongs to a user and a dog. So, a journal entry will have the user_id and dog_id stored in the journal_entries table. Diet and exercise entries belong to a journal entry. The journal_entry_id will be stored in the exercise_entries and diet_entries table.

What are params? What are the two places they come from? 

	Params are a user sending data to my web application. Params get this data from a form a user filled out or from the url itself. 

What are sessions?

	Sessions is a hash that stores data on the server and passes that information to the user in a cookie. The session_id acts like a key and is unique to a users session. 

What is the flow of your application? (i.e. what triggers your get routes vs post routes or patch routes or delete routes)

	A user signs in, a get route is sent which triggers my site#index action in the site_controller and renders the home page view. A user can go to their profile page which sends a get route, triggering the users#show action in the users_controller to render the users show page. From that point a user can create a new dog. sending off a get route, triggering  the dogs#new action in my dogs_controller, rendering a new dog form. Once the user submits the form a post route is sent and triggers the dogs#create action. Or, from the profile page a user can update a journal entry sending a get route that triggers the journal_entries#edit action in the journal_entries_controller. Once they submit the edit form for the journal entry a patch route is sent, triggering the journal_entries#update action.  If they decide to delete a journal entry from the profile page a delete route gets sent triggering the journal_entries#destroy action. 

How do you authenticate your users when they log in?
	
	A user is authenticated when they enter their password into my app. The password entered is salted and compared to the salted password in the database associated with said user. Authentication between my app and the user is then stored in a session id stored in a session hash placed in a unique cookie saved in the users browser. 

How do you validate that a username is unique? 

	My app uses the Devise gem which validates a users uniqueness by email. The devise validatable module is included in my User model and “automagically” validates users uniqueness by email.

Why do I need to check that a resource belongs to the current user in the patch and delete routes?

	You want to check that a resource belongs to the current user because you don’t want a user to be able to update or delete other peoples resources. 

What are URL helpers? Where do they come from?

	URL helpers are are there so we don’t have to hard code route paths. One benefit is it helps clean up the view and controller code. The URL helpers come from Rails router and are named in the route prefix.

When do we typically use form_for vs. form_tag?

	form_for and form_tag are available in my application due to ActionView, a sub gem of Rails. After researching form_tags again I came across something I forgot, Rails helps prevent Cross Site Request Forgery by default. The way it does this is by requiring a unique authenticity token be submitted with each form. But, to finally answer the question you use a form_for when building a form for an object. You would use form_tag when your form is not handling an object, ex: search forms. 

How does omniauth work?
	
	I believe OmniAuth has been created for those users who will refuse to use your application because they don’t want to set and remember another password.   Omniauth makes use of third party websites for logging in to your application. 

When a user makes a request (via form, link, manual change in the url), how does rails know how to handle that request?

	When my application receives a request the routing will determine which controller and action to use. Rails creates an instance of the controller and runs the method with the same name as the action. This is why my controllers should inherit from ApplicationController.

How do you validate data? When are these validations run?

	Validations are used to ensure valid data is saved into your database. Validation can be run many ways but Model-level validations are the best way to ensure only valid data is saved into your database. You can also create your own validation methods in a model. Validations are typically run before SQL UPDATE and INSERT commands are sent to the database. 
	

Why do we use a join table? What relationship are we setting up?

	A join table is used to reference associated data through the use of foreign keys. In my join table I am setting up relationships for a journal entry. A journal entry belongs to a user and their dog. So the journal_entries table has a user_id and dog_id column. Each journal entry instance will have a user_id and dog_id saved. 

How do we set up nested forms - what do these forms need to include so that we can associate the new object with the existing? (i.e. if we have the nested route: posts/1/comments/new, how do we associate the new comment with post with id of 1?)

	We need a has_many and belongs_to association. In my app I have a nested form for a journal entry. The nested forms are for diet and exercise entries. My routes look like this “…/users/1/dogs/1/journal_entries/new.” So in my JournalEntriesController I have to set the associations before rendering the form. My controller has to know of the current_user and that users dog in the new action. Then I have to build a journal entry instance on the current users dog object. So a journal entry will have a user_id and a dog_id set before it is saved into the database. For Diet and exercise entries I build an association to the journal entry. Dogs have a diet and exercise entry through a journal entry. So the journal_entry ID is saved in the diet and exercise table. 


Are nested routes and the forms on those nested routes connected in any way? How do we use a nested route to help set up our form?

	form_for automatically performs a route look up to find the right URL for the object. In that way a nested form is connected to a nested route. 



