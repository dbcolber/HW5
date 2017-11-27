# SI 364 - Final Project questions

## Overall

* **What's a one-two sentence description of what your app will do?**
The app will ask the user to enter a ingredient/recipe search term and will use the Food2Fork API to return recipes for the user. The recipe and user data will be stored in a SQL database and build a virtual cookbook with each query the user enters.

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
1) Search model fields: id, search term, count, recipe titles, recipe urls, user_id
2) Recipe model fields: id, search term, recipe title, recipe url, image url, publisher, user_id
3) User model fields: user_id, name, email

* **What uniqueness constraints will there be on each table? (e.g. can't add a song with the same title as an existing song)**
The user cannot add an ingredient/recipe query that they have already added. This is because the application will be building a virtual cookbook of sorts and if the user has already searched for 'chicken', then they shouldn't readd the same recipes.

* **What relationships will exist between the tables? What's a 1:many relationship between? What about a many:many relationship?**
1:many - Search term in the Search model will have a 1:many relationship with all recipes in the recipe model that were produced from that search term

Many:many - Many search terms and recipes can be associated with mulitple users

* **How many get_or_create functions will you need? In what order will you invoke them? Which one will need to invoke at least one of the others?**

1) get_or_create_user - this function will be invoked first so that the search and recipe data can be associated with the distinct user
2) get_or_create_search - this function will be invoked next and will check the db to see if the search term has already been inputted by the user or not. If not, the search data will be added to the table
3) get_or_create_recipe - this final function will add the resulting recipes produced by the search term to the database so that each recipe has its own row in the db. If one of the recipes has already been added, such as if the user typed "chicked" and got a recipe titled "Mexican Chicken Enchiladas" and then later searched specifically for enchiladas, then the db will not readd this recipe since it already exists in the recipe model.

## The Pages

* **How many pages (routes) will your application have?**
1) Index / where user enters recipe search term
2) Search term results (will show the top few recipes associated with their search term)
3) Virtual cookbook (collects all recipes that have resulted from the user's query history)
4) (Still considering including this one) Individual pages for each recipe
5) 400 error
6) 500 error

* **How many different views will a user be able to see, NOT counting errors?**
1) The first view will show the user the recipes that result from their search term, including the recipe title, a link to the recipe information, an image of the recipe, and any other critical information the API provides.
2) The second view will be of the virtual cookbook and will show a list of the recipe titles that have been produced from ther user's queries. The user will be able to click on a title/dynamic link to take them to the thrid view.
3) This view is of all details pertaining to a single recipe. This includes title, recipe details, and a picture of the recipe.

* **Basically, what will a user see on each page / at each route? Will it change depending on something else -- e.g. they see a form if they haven't submitted anything, but they see a list of things if they have?**
See answers to previous two questions

## Extras

* **Why might your application send email?**
To send the user recipe information pertaining to their latest query

* **If you plan to have user accounts, what information will be specific to a user account? What can you only see if you're logged in? What will you see if you're not logged in -- anything?**
Each user account will be defined by the user's email. The email will hold the recipe data pertaining to the user.

* **What are your biggest concerns about the process of building this application?**
I'm wondering what the best way to integrate user auth. into this app is. I want each user to be able to save their recipes to their account, but i'm wondering if I need a separate user login page or if it would be sufficient for the user to just state their email when searching for recipes, and that would define which user is interacting with the application. 
