# SI 364 - Final Project questions

## Overall

* **What's a one-two sentence description of what your app will do?**
The app will ask the user to enter a ingredient/recipe search term and will use the Food2Fork API to return recipes for the user. The recipe and user data will be stored in a SQL database.

## The Data

* **What data will your app use? From where will you get it? (e.g. scraping a site? what site? -- careful not to run it too much. An API? Which API?)**
The Food2Fork API

* **What data will a user need to enter into a form?**
1) Recipe search term
2) If they want to sort by rating or trend
3) User's name
4) The user's email (to send recipe details to)

* **How many fields will your form have? What's an example of some data user might enter into it?**
3 StringFields:
  1) Recipe search term (ex: 'Chicken' or 'Guacamole')
  2) Sorting preference (ex: 'r' for rating (user will be instructed as to their options for sorting))
  3) User's name
  4) Email (ex: danielle123@yahoo.com)
1 SubmitField('Submit) to submit form

* **After a user enters data into the form, what happens? Does that data help a user search for more data? Does that data get saved in a database? Does that determine what already-saved data the user should see?**
After a user enters the data into the form, the application will make a call to the Food2Fork API to pull recipe results related to their search term. The user will see a list of a few of the top recipes, including recipe title, a dynamic link to the lrecipe, and an image of the recipe. A personalized email of this information will be sent to the email provided.

* **What models will you have in your application?**
1) Search model
2) Recipe model
3) Uesr model

* **What fields will each model have?**
1) Search model fields: id, count, recipe titles, recipe urls
2) Recipe model fields: id, recipe title, recipe url, image url, publisher
3) User model fields: id, name, email

* **What uniqueness constraints will there be on each table? (e.g. can't add a song with the same title as an existing song)**

* **What relationships will exist between the tables? What's a 1:many relationship between? What about a many:many relationship?**

* **How many get_or_create functions will you need? In what order will you invoke them? Which one will need to invoke at least one of the others?**

## The Pages

* **How many pages (routes) will your application have?**

* **How many different views will a user be able to see, NOT counting errors?**

* **Basically, what will a user see on each page / at each route? Will it change depending on something else -- e.g. they see a form if they haven't submitted anything, but they see a list of things if they have?**

## Extras

* **Why might your application send email?**

* **If you plan to have user accounts, what information will be specific to a user account? What can you only see if you're logged in? What will you see if you're not logged in -- anything?**

* **What are your biggest concerns about the process of building this application?**
