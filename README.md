# Python-Live-Project

#### OVERVIEW
For the Python Live Project, I worked a two week sprint on scrum team developing a web application within the Django Framework. The main app hosts a variety of sub-apps pertaining to individual hobbies. I developed a sub-app called GardenApp, building in CRUD functionality. The GardenApp allows users to store information about their individual vegetables into two databases, one pertaining to planning each vegetable (growing zone, sowing time frame, general care needs); and another that tracks each vegetable throughout the growing season and harvest (harvest yield, observations, weather events, etc). As repository, the GardenApp allows users to pull up relevant information across years either for reuse or to compare data like harvest yields, techniques that worked, didn't work, or environmental factors such as a major weather event that may have played a role in harvest production.

![](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Images/home.png)


#### Models & Forms
I created two models to map to two databases. The attributes in class Planner correspond with preseason garden planning, and attributes in class Tracker correspond to tracking data during the growing season and during harvest. In the code snippet below, the zone type attribute has a tuple that correlates to the the choice field, allowing users to choose from the provided growing zones. The class Tracker is connected to class Planner via a foreign key. This ensures users can pull up the same vegetable on their tracker form as their planner form, and add additional information. I had originally assigned a primary key (pk) on class Planner not realizing Django automatically assigns pk's. Once I deleted the pk, both tables connected in the database.

I then created a forms.py and functions to render the forms to their corresponding templates. In forms.py, I utilizied widgets for suggestions on user input, and imported layout to render the form as a crispy form. In this early stage, I learned the importance of indentation in developing functions, as one of my else statements that accounts for user spaces or blank inputs did not initially work when it was indented too far. 

- [MODELS: modelforms](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Code%20Snippets/GardenApp_models.png)

- [FORMS: form layouts & widgets](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Code%20Snippets/GardenApp_forms.png)

- [VIEWS: render forms](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Code%20Snippets/GardenApp_renderforms.png)

![](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Images/form.png)


#### Display All Items from Database

After the forms rendered and user input saved successfully to the database, I created function that gets all items from the database and sends them to the allvegetables template which is linked from the home template as “Your Garden”. This template displays all vegetables and minimal data from both databases.

- [VIEWS: display all and details](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Code%20Snippets/GardenApp_displaydetails.png)
- [TEMPLATE: display all](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Code%20Snippets/GardenApp_displayalltemplate.png)

![](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Images/displayall.png)


#### Details, Edit & Delete
From the allvegetables template, users can select an individual vegetable either from the Planner or Tracker table that renders onto a details template displaying all the information the user has submitted. The function to render the corresponding templates matches a pk argument in URL which selects an individual vegetable based on id, and also raises a 404 error if selected object does not exist. Aside from the get_object_or_404 method, I also used the objects.all() method so both templates would pull the corresponding information from the other database if the data exists. Both templates are inverse each other so users have access to both data tables regardless of which table they select from the allvegetable template.

![](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Images/details.png)


In the details page, users also have the option to select edit or delete on the Planner and Tracker details. Like the details template, a pk is assigned to match the url calling the right function. However, the edit functions also pass an instance in the form POST request, so the form is populated with data the user already submitted.

- [VIEWS: edit forms](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Code%20Snippets/GardenApp_editforms.png)
- [VIEWS: delete forms](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Code%20Snippets/GardenApp_deleteforms.png)

![](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Images/edits.png)
![](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Images/delete.png)

#### API
This completed Django CRUD functionality. From here I began a user story starting to connect to an external API. I chose the Trefle API which is a botanical database hoping to let users search for specific plants and their information, saving them to the GardenApp for additional information. I successfully connected to the API and rendered information along with corresponding images. But did not complete the user search feature with the given time. This is a task I plan to return to when I finish the full stack bootcamp. 
![](https://github.com/esievaughn/Python-Live-Project/blob/main/GardenApp%20Images/apipng.png)

#### Conclusions
This project was instrumental in my understanding of Django and working on a scrum team. I enjoyed daily standups and working out roadblocks on slack as needed. This project was the first time I used Azure, and I appreciated its ease of use in grabbing user stories and VCS. In a short period, I went from piecemealing a Django app with limited understanding of how everything actually connected to feeling confident in developing the front and back end of an app.
