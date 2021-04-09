# MVC-Slides-Notes


LEON CLASS APRIL 8

Browser looks at router

	

Controller is the middle man
	do I need to talk to the database?
	because if I need to, the model is going to handle that.

	Model takes the data and hands it off to the view

Html then sends it back to the browser


The view and the model never talk to each other .

<img width="601" alt="Controller" src="https://user-images.githubusercontent.com/33885541/114113837-74f92980-9894-11eb-96f2-e17be6021b5b.png">

￼

Does it matter how my data is set going into and out of the database?	no.

Model-database can be crazy an the view wouldn’t know.

The view on the left is ejs, with react in the future

If we can separate out the pieces
Doesn’t matter which piece we wind up using
If I want to swap ejs for pug or handlebars
Does the rest of the project care? Nope


Nodemon restarts your server when you save files. 
So if server.js is saved in 
<img width="574" alt="name todolist-review-app" src="https://user-images.githubusercontent.com/33885541/114113910-94905200-9894-11eb-803c-533514b3e20c.png"><img width="346" alt="license ISC" src="https://user-images.githubusercontent.com/33885541/114113958-a540c800-9894-11eb-91ed-8b717d4b916b.png">


￼

npm start
	see its connected to database
	
<img width="406" alt="watching path(s)" src="https://user-images.githubusercontent.com/33885541/114113973-ad006c80-9894-11eb-8bda-b7dfcfdbdb6e.png">

￼

Config folder has .env and database.js
	
<img width="328" alt="scripts" src="https://user-images.githubusercontent.com/33885541/114113993-b7bb0180-9894-11eb-8f91-a27cefa131c3.png">
￼

Some people run some things when developing and other things while debugging/running
	
controllers folder, models folder, public, routes, and views.


<img width="146" alt="Screen Shot 2021-04-08 at 4 19 11 PM" src="https://user-images.githubusercontent.com/33885541/114114023-c6091d80-9894-11eb-8841-b89d42513453.png">

￼

Mongoose used to make a connection to mongo database.
In database.js which is in config folder with .env

Going to run connectDB() and that’s going to run our connection to our database

The below is exporting a function (async)
and then we’re calling it 

<img width="788" alt="Screen Shot 2021-04-08 at 4 22 57 PM" src="https://user-images.githubusercontent.com/33885541/114114037-cf928580-9894-11eb-8374-18239c1678d1.png">


Need to create .env file with Leon’s code

WHAT IS MONGOOSE? Explain


Using port as below, not a const PORT at the top as before.  This shows where the port is in our files.
￼
<img width="567" alt="homeRoutes)" src="https://user-images.githubusercontent.com/33885541/114114071-e0db9200-9894-11eb-9163-de64ae95ed76.png">




routes:
Look at the request and figure out which controller should be handling that request.
	controller is middleman that chooses to talk to database, whatever.  
	routes see the URL, see the request, and they hand the request off to a specific controller

	
￼<img width="714" alt="const app = express()" src="https://user-images.githubusercontent.com/33885541/114114088-e933cd00-9894-11eb-983c-a174bc3936eb.png">


In Routes folder is home.js:
	only doing one thing - file sees the route and tells what controller to run.
	routes are just doing that one thing.
	homes controller for home page
	actually to do list, going to have controller that handles deleting, updating, all that stuff.  Starting to separate out applications.
	it says you have a request coming in on the main route (line 5), then go to controllers/home to find it
￼
<img width="714" alt="Screen Shot 2021-04-08 at 4 27 25 PM" src="https://user-images.githubusercontent.com/33885541/114114102-f2bd3500-9894-11eb-970c-aaf051cfce35.png">




This is spitting out an object:
	which has a method
	getIndex is set equal to a function
	getIndex is a method.
  
  
  
<img width="511" alt="Screen Shot 2021-04-08 at 4 29 16 PM" src="https://user-images.githubusercontent.com/33885541/114114112-fa7cd980-9894-11eb-8101-2b9a21db7f4c.png">

￼

DONT FREAK OUT! We’re just putting objects and functions into their own folders

Our user made a request in the browser - how?
	GET request

what is router trying to figure out based not his request? Which controller is going to handle this request. THATS IT. Going to figure out which controller is going to handle this request.
	
which controller did the router pick to handle the request?	HOME controller.

HOME controller heard the get request, and when it heard it, what did it do?
	sent to views - told the views to render it.

Once view is rendered, what did the controller do with the view that was rendered?
	RESPONDED

Here it is: 
￼
<img width="494" alt="Screen Shot 2021-04-08 at 4 34 25 PM" src="https://user-images.githubusercontent.com/33885541/114114133-08caf580-9895-11eb-89f5-c992133963e8.png">



User made a request, made its way to our server - and first the router had to send it to the right controller. Handed it off to the HOME controller. Home controller knew what to do. “Hey EJS, render me some HTML”. Once EJS did, the controller RESPONDED with it back to the browser

￼
<img width="606" alt="Browser" src="https://user-images.githubusercontent.com/33885541/114114139-0f596d00-9895-11eb-9d4c-729ccaf693c5.png">



Below in row 16 is the beginning of our router:


<img width="731" alt="Screen Shot 2021-04-08 at 4 35 58 PM" src="https://user-images.githubusercontent.com/33885541/114114149-1a140200-9895-11eb-9486-84b8c99397a3.png">


￼
	whenever there’s a request on the Amin route, which router file is going to handle it? 
	/routes/home.js

Here’s home.js


<img width="572" alt="const router = express  Router()" src="https://user-images.githubusercontent.com/33885541/114114165-24360080-9895-11eb-92f4-6cfb00244855.png">



￼
Ok made a request on the main route, which controller are we going to talk to? homeController

Now which method are we going to use from this homeController?

getIndex:


<img width="427" alt="Screen Shot 2021-04-08 at 4 37 31 PM" src="https://user-images.githubusercontent.com/33885541/114114189-3021c280-9895-11eb-9270-8ab303fcb5a9.png">


￼
getIndex request and response 


BROWSER MADES GET REQUEST ROUTER HEARD IT
SENT TO CONTROLLER
MADE THE VIEW DO IT
RESPONDED BACK TO BROWSER

Ok so did the main route, what happens when click on link?

GET request (can see in inspect) - its a get on the TODOS route

<img width="611" alt="Create A Todo List" src="https://user-images.githubusercontent.com/33885541/114114202-3a43c100-9895-11eb-9ddf-57b5343b00e7.png">




￼
	(opens the list) as below
  
  <img width="292" alt="First Try  Delete" src="https://user-images.githubusercontent.com/33885541/114114205-3f087500-9895-11eb-8ae7-29be72fc3092.png">

￼
	GET Request was the link

Go to todos:


<img width="599" alt="Screen Shot 2021-04-08 at 4 52 13 PM" src="https://user-images.githubusercontent.com/33885541/114114219-4596ec80-9895-11eb-8557-15c9ef1ea49a.png">

￼
Line 15 hears todos


<img width="481" alt="const homeRoutes require( routeshone')" src="https://user-images.githubusercontent.com/33885541/114114230-4c256400-9895-11eb-9d29-e5ee054d9288.png">



￼
We already said we’re on the todos route.
Since we’re already on it, we don’t have to do todo/create, todo/etc

Since we’re in todos…. Dont need to

TOO FAST TOO FAST

<img width="595" alt="Screen Shot 2021-04-08 at 4 53 05 PM" src="https://user-images.githubusercontent.com/33885541/114114264-62332480-9895-11eb-8006-0995486d78db.png">




￼

The route for all the todos will be in the todos file:


<img width="500" alt="Screen Shot 2021-04-08 at 4 54 09 PM" src="https://user-images.githubusercontent.com/33885541/114114280-68c19c00-9895-11eb-873e-dc04793d69b5.png">

￼

Controllers, todos:
￼


<img width="506" alt="const express a require('express')" src="https://user-images.githubusercontent.com/33885541/114114291-6f501380-9895-11eb-94bd-c1d7bffe6f73.png">


What is the todos controller spitting out?
5 methods!


<img width="592" alt="Screen Shot 2021-04-08 at 4 55 23 PM" src="https://user-images.githubusercontent.com/33885541/114114303-76772180-9895-11eb-832e-ab892fe84a19.png">



￼
The controller is the ONLY THING thats talking to the model (model is line 1)

Todos herd the request on the main route, went to the todosController, since we’re on the main route GET from todos, we run todosController and getTODOS

getTodos is our asynchronous request
	
what are these 2 lines doing?

<img width="607" alt="Screen Shot 2021-04-08 at 4 56 51 PM" src="https://user-images.githubusercontent.com/33885541/114114358-8db60f00-9895-11eb-85a9-5a805b2a3643.png">




￼
We have this Todo variable that is requiring our Todo model

In our models folder we have Todos
	in our model we need mongoose to talk to db
  
<img width="549" alt="type String," src="https://user-images.githubusercontent.com/33885541/114114374-96a6e080-9895-11eb-8920-315f01699eca.png">
  
  
  
￼
We have a model, a schema, then we’re exporting the model

WHAT IS A SCHEMA??

	

Right now my objects have 2 pieces of data:
	the todo, and whether or not its completed
  
<img width="488" alt="required true," src="https://user-images.githubusercontent.com/33885541/114114408-a45c6600-9895-11eb-832b-de54edc7484a.png">
  
  
￼

If we’re working on a large project we’re going to have lots of different models. Mongoldb doesn’t force you to have any structure to the stufff you’re putting in your database.
	why is this a horrifically bad idea?
		no consistency!! If I put a number into the list, how do I know its a number? How do I know completed is a boolean? I might have to write more logic to make sure that my types are correct. Might have to write more logic to cover my butt in case we’re working together and you store something inappropriate…
	schema gives what you put in MongoDB a consistent, repeatable structure.
	in above code, we know completed is a boolean

I know the only way I’m talking to the database is through my MODEL
	This is my todo MODEL

I can come into the model and look at it. NOTHING ELSE IS INTERACTING WITH MY DATABASE.
￼
<img width="602" alt="Screen Shot 2021-04-08 at 5 02 52 PM" src="https://user-images.githubusercontent.com/33885541/114114428-b0e0be80-9895-11eb-8c82-b1dcf95b08ae.png">

Request Heard by router
	its a todo route, so its handled by the todo route file
	its a get request on the main route, we know which controller should handle this, the Todos controller, and specifically I want the get todos method to run
	we look at the getTodos method
	its going to go and find all the documents. But are we hard coding db.collection? How does it know where to go find it? What is it using? TODO MODEL
	TODO model is what allows us to talk to the database
	since we’re using mongoose and not MongoDB, mongoose gives us some goodies. Going to be a way for us to do more in the long run.
	MonGOOSE IS CALLED SOMETHING. It’s not just MONGODB, something that helps us use MONGODB
	using the model to go find all our document:
  
  
  
  <img width="612" alt="Screen Shot 2021-04-08 at 5 05 57 PM" src="https://user-images.githubusercontent.com/33885541/114114457-bdfdad80-9895-11eb-81ab-4f62fa29db9a.png">

￼
What’s missing above in row 6? We don’t have to.array
	because we’re using mongoose it returns an array already.

todoItems is an array of objects without needing to.array
Using the model we’re going back to find all the documents where completed is false (ROW 7)
	then controller is going to tell our EJS to render, its going to pass in all the items, all the are left, it spits out!
	
clicking the link - the anchor tag - made a request to localhost2121todos
 todos? I know which to use! Todos router file and on main path. Which controller? todoController
because we used the getTOdos Method on the controller
how were we able to talk to the database? Using what? MODEL
view rendered out some html then the controller RESPONDED with that HTML

Ok now we entered “GET OAT MILK”
￼
<img width="470" alt="Get Oat Milk Delete" src="https://user-images.githubusercontent.com/33885541/114114520-dbcb1280-9895-11eb-9ed0-addbcd8b353a.png">



How do we know that?
	because we CREATED SOMETHING
	always posting with forms
	
Lets look at this in the todos.ejs (under views folder)
	(also in views folder is index.ejs
  
  <img width="601" alt="Screen Shot 2021-04-08 at 5 11 22 PM" src="https://user-images.githubusercontent.com/33885541/114114538-e8e80180-9895-11eb-9748-7071d833d675.png">

  
￼
We know that when we submit the post, we are making a post request to what route: TODOS

We hear a todos request come in, gets handed off to the todosRoute

<img width="477" alt="Screen Shot 2021-04-08 at 5 12 18 PM" src="https://user-images.githubusercontent.com/33885541/114114562-f2716980-9895-11eb-8a8a-e0c7af66748b.png">



￼
Go to todosroute:

<img width="595" alt="Screen Shot 2021-04-08 at 5 12 32 PM" src="https://user-images.githubusercontent.com/33885541/114114574-f8674a80-9895-11eb-8411-5bd2b1790ea0.png">

￼
Is it a createTodo? (Line 7)
	so whenever we hear a createTodo request (post request)
	going to todos controller and use the createTodo method
	here it is:
  
  
 <img width="602" alt="Screen Shot 2021-04-08 at 5 13 14 PM" src="https://user-images.githubusercontent.com/33885541/114114594-04eba300-9896-11eb-875e-37341d67c5e3.png">

￼
It’s going to create a new todo using the what?
	what do I have to be worried about ? Random stuff. Don’t want anyone to interact with my code unless its through a model. Dont want to handle rogue requests to my database.
Where did req body come from?
FORM! (As below)
￼
<img width="593" alt="Screen Shot 2021-04-08 at 5 15 12 PM" src="https://user-images.githubusercontent.com/33885541/114114611-0d43de00-9896-11eb-982a-76dd0a3f3490.png">



Can grab the todo item out of the body which came with the request
	grabbed it… used it to create my document in my database:
  
  
<img width="612" alt="Screen Shot 2021-04-08 at 5 15 40 PM" src="https://user-images.githubusercontent.com/33885541/114114629-146aec00-9896-11eb-8892-ccde585dc318.png">

￼
After creating that document - line 17 - RELOADED
	when reloading 

Route heard get request, its the main page on the todos route, 
Going to use todos controller with the get todos method

Sends that response back to the user

<img width="596" alt="Screen Shot 2021-04-08 at 5 16 40 PM" src="https://user-images.githubusercontent.com/33885541/114114653-1df45400-9896-11eb-9af3-f007f77726c8.png">


￼

Ok deleted firsttry:

<img width="567" alt="Get Oat Milk Delete" src="https://user-images.githubusercontent.com/33885541/114114670-29e01600-9896-11eb-81c0-f827feae3877.png">

￼
Only thing that can hear that click is the client side javasript
So lets look at client side javascript in our folder:
	main.js
￼
<img width="608" alt="Screen Shot 2021-04-08 at 5 18 56 PM" src="https://user-images.githubusercontent.com/33885541/114114689-35334180-9896-11eb-9f0f-9c6f42bafd35.png">




If we look at the EJS, 

<img width="586" alt="Screen Shot 2021-04-08 at 5 19 10 PM" src="https://user-images.githubusercontent.com/33885541/114114705-3cf2e600-9896-11eb-8f08-2fc6d8eec581.png">


￼
Grab the delete, going to add the deleteTodo function
	going to grab the todo that I tried to delete by grabbing this.parentNode.dataset.id (this is a jump to a better understanding)
	clicked on delete. That was a span. What is the parent nod of the span?
	THE LI
	what is dataset id?
  
  <img width="599" alt="Screen Shot 2021-04-08 at 5 20 12 PM" src="https://user-images.githubusercontent.com/33885541/114114721-4714e480-9896-11eb-9ae3-f42e4b0c6190.png">

  
￼
As above - data id = ZEBRA (whatevs)
	called it data ID.
	what did I plug in as the value?	
	used the ID from the document

Every time I create a document in MongoDB:

<img width="291" alt="todolist todos" src="https://user-images.githubusercontent.com/33885541/114114741-5136e300-9896-11eb-96a6-5b94f74dec49.png">

￼
We get that big long id
It’s unique for every document
So what was the problem we were running into with older version of todo list?

This ensures that only that ID is deleted, not any document that says the same thing. ID is unique.
	it’s a data attribute in the HTML now, it’s going to have a new ID with each thing… 
	every document will be unique, every LI will be unique (even if the words are the same), 	
	in main.js can do DATASET:
  
  <img width="578" alt="Screen Shot 2021-04-08 at 5 24 50 PM" src="https://user-images.githubusercontent.com/33885541/114114758-5ac04b00-9896-11eb-876e-3118562d749a.png">

￼
	if I write dataset.rainbow then in the other file it should be data-rainbow.  They need to be the same.


Is el.completed === true? Then put in completed
If it’s false - put in not’

Using this to tell if the span class is completed or not:

<img width="602" alt="Screen Shot 2021-04-08 at 5 29 39 PM" src="https://user-images.githubusercontent.com/33885541/114114773-657ae000-9896-11eb-8bb6-6bebf5cc8781.png">

￼

Can see it here in the Dom inspector:

<img width="602" alt="Todos" src="https://user-images.githubusercontent.com/33885541/114114781-6ad82a80-9896-11eb-9259-516536b8ff39.png">

￼
The ternary is what’s changing it from not to completed. It’s just a short one line conditional? Is it? Yes  do this. Not do that.

It’s just a cooler way than writing it this (old) way:

<img width="270" alt="Screen Shot 2021-04-08 at 5 31 42 PM" src="https://user-images.githubusercontent.com/33885541/114114795-71ff3880-9896-11eb-9dc0-a5fc56cc6abb.png">

￼

Last thing I do is plug in the todo text (line 15.5):

<img width="593" alt="Screen Shot 2021-04-08 at 5 32 12 PM" src="https://user-images.githubusercontent.com/33885541/114114802-77f51980-9896-11eb-9582-7f991b874e4f.png">

￼


Now going to make a delete request
Going to pass along this info: row 24

<img width="596" alt="Screen Shot 2021-04-08 at 5 34 35 PM" src="https://user-images.githubusercontent.com/33885541/114114824-82afae80-9896-11eb-8052-ed113cb70a0b.png">

￼

Deciding what to do..... 

<img width="591" alt="Screen Shot 2021-04-08 at 5 35 07 PM" src="https://user-images.githubusercontent.com/33885541/114114837-88a58f80-9896-11eb-8bfb-0c99956df675.png">

￼

Delete todo method
	find the id todoIdFromJSFile
Using model talk to database, find one where ID matches that ID and delete it.
<img width="503" alt="console  log(err)" src="https://user-images.githubusercontent.com/33885541/114114858-922ef780-9896-11eb-9f34-7dd5d058805d.png">

￼
Console logged so you can see it’s the ID number:
￼
<img width="264" alt="Server 15 running, you better catch it!" src="https://user-images.githubusercontent.com/33885541/114114873-99560580-9896-11eb-8c08-6c9e1ed6364b.png">


When done respond to fetch saying I deleted it - async resolves - RELOAD
	RELOAD is new Get request
	ON THE TODOS ROUTE
  
  <img width="595" alt="Screen Shot 2021-04-08 at 5 36 51 PM" src="https://user-images.githubusercontent.com/33885541/114114885-a115aa00-9896-11eb-9b88-71a825054f4a.png">

  
  
￼
Server said oh its a todos route....
TOO FAST TOO FAST 


<img width="484" alt="const todoltens = await Todo  find()" src="https://user-images.githubusercontent.com/33885541/114114912-ae329900-9896-11eb-87f2-0b19b7f25cd8.png">





Too fast too fast
￼

Build all our LI’s: when controller is done it’s finished rendering out that THML and we respond WITH IT

<img width="586" alt="Screen Shot 2021-04-08 at 5 38 04 PM" src="https://user-images.githubusercontent.com/33885541/114114933-bbe81e80-9896-11eb-8da7-f2951f8cd718.png">


Cientside javascript:
It had the not class, so going to run the markComplete function:

<img width="597" alt="Screen Shot 2021-04-08 at 5 44 51 PM" src="https://user-images.githubusercontent.com/33885541/114114957-c4d8f000-9896-11eb-8aab-4bbcbf7b6a43.png">


￼
markComplete looks at the span that held the text…

<img width="478" alt="headers (Content-type' 'applicationjson')," src="https://user-images.githubusercontent.com/33885541/114114975-cdc9c180-9896-11eb-8c3d-a521ef7807c2.png">

￼
The ID is unique even though both text say the same thing:

￼<img width="246" alt="QUERY RESULTS 1-2 OF 2" src="https://user-images.githubusercontent.com/33885541/114114989-d3270c00-9896-11eb-95bc-9418c23b8fed.png">


Grabbing the ID
Making a fetch to my todos/markComplete route, and its a PUT

Going to the todosController and the markComplete method
￼
<img width="586" alt="Screen Shot 2021-04-08 at 5 47 20 PM" src="https://user-images.githubusercontent.com/33885541/114115034-e33eeb80-9896-11eb-8e71-1decae5e6ffe.png">


Use model to go into the database, find something that has the ID and set completed to true (or false)

<img width="491" alt="console  log(err)" src="https://user-images.githubusercontent.com/33885541/114115050-eafe9000-9896-11eb-9adf-788618e1a999.png">


￼
Fetch resolves
We make a GET (reload)


Now we can have duplicates and not worry - using the IDs

REMEMBER NPM INSTALL
Setup ENVIRONMENT VARIABLES

Thats it!

TRY Creating a lecture around what is MVC and USE THIS CODE

