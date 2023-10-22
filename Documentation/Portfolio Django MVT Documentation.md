# Portfolio Django MVT Documentation

### Table of Contents

[Introduction](#introduction)

[Part 1: Implementing Generic List and Detail Views in Django](#implementing-generic-list-and-detail-views-in-django)

&nbsp;&nbsp; [Implementing a ListView](#implementing-a-ListView)

&nbsp;&nbsp; [Implementing a DetailView](#implementing-a-DetailView)

&nbsp;&nbsp; [More Explanations](#more-explanations)

[Part 2: Implementing Forms in Django](#implementing-forms-in-django)

&nbsp;&nbsp; [General Setup for Django Forms](#general-setup-for-django-forms)

&nbsp;&nbsp; [Creating Items via Forms](#creating-items-via-forms)

&nbsp;&nbsp; [Updating Items via Forms](#updating-items-via-forms)

&nbsp;&nbsp; [Deleting Items via Forms](#deleting-items-via-forms)

[Part 3: Deploy Django Web App on Replit](#deploying-a-django-web-app-on-replit)

[Part 4: Modifying User Interface in a Django Web App](#modifying-user-interface-in-a-django-web-app)

&nbsp;&nbsp; [Adding Buttons and Styling to Make Navigation Better](#adding-buttons-and-styling-to-make-navigation-better)

&nbsp;&nbsp; [Adding Dark Mode Functionality](#adding-dark-mode-functionality)

[Resources](#resources)

### Introduction

This document is the compilation of the documentation created for GE05 (parts 1-4). In each part, I will include who is responsible for the information to give credit where it is due. After reading this documentation you should be able to understand how to implement generic list/detail views and forms in Django, as well as how to deploy the app on Replit and customize the user interface (found in Django templates).

### Implementing Generic List and Detail Views in Django

As a part of the Django framework, there are generic display views called `DetailView` and `ListView` that display a list of objects and information contained within them based on a database model. In short, when using these provided views Django fetches information from the database, renders it in a template, and displays the objects/details to the user. You would use a `ListView` whenever you want to present a list of objects within a database model; you would use `DetailView` whenever you want to display the object's related members.

Before you can display database information to the user in a web app, you must have some models defined in `models.py` to store data.  An example of a model in our Portfolio App is shown below.

```python
class Portfolio(models.Model):
    title = models.CharField(max_length=200, blank=False)
    contact_email = models.CharField(max_length=200, blank=False)
    is_active = models.BooleanField(default=False)
    about = models.CharField(max_length=200, blank=True)    # Optional char field

    def __str__(self):
        return self.title

    def get_absolute_url(self):
        return reverse('portfolio-detail', args=[str(self.id)])
```

Looking at the model above, the model has various model members such as a `title`, `contact_email`, `is_active`, and `about`. All of these members make up the details of a sudent portfolio object within the database. On the web app, we want to display both the objects themselves and the details contained within them, this is where Django's generic `ListView` and `DetailView` come into play.

*Accreditation: Tyler Carroll & Matheus Abrantes*

#### Implementing a `ListView`

To display this information using a generic display view, we add a view to `views.py` (shown below).

```python
class PortfolioListView(generic.ListView):
  model = Portfolio
```

Then, we add a path variable in `urls.py` to map the view to a URL (shown below). This ensures the correct view gets displayed when a user accesses a particular URL or clicks a button that redirects them.

```python
urlpatterns = [
   path('portfolios/', views.PortfolioListView.as_view(), name= 'portfolios'),
]
```

Finally, we create a template to render the view (shown below).

```html
<!-- inherit from base.html -->
{% extends 'portfolio_app/base_template.html' %}

{% block content %}
  <h1>Computer Science Student Portfolios</h1>

  <h2>List of Students with Active Portfolios</h2>
  {% for portfolio in student_active_portfolios %}
  <li class="list-group-item">Name: {{portfolio.name}}
  <p><strong>Portfolio: {{ i.portfolio.title }}</strong>
  <a class="btn btn-primary" href="{{ i.portfolio.get_absolute_url }}" role="button">View</a>
  </li>
  {% endfor %}
  </ul>
{% endblock %}
```

*Accreditation: Tyler Carroll & Matheus Abrantes*

#### Implementing a `DetailView`

Similar to [Implementing a `ListView`](#implementing-a-ListView), to create a `DetailView` we add a view to `views.py`.

```python
class PortfolioDetailView(generic.DetailView):
  model = Portfolio
  def get_context_data(self, **kwargs):
    context = super(PortfolioDetailView, self).get_context_data(**kwargs)
    projects = Project.objects.filter(portfolio_id=self.object)
    context['projects'] = projects
    return context
```

Above, you can see we overrided  `get_context_data()` to customize the data that gets passed to the template.

Just as before, we add a path to `urls.py`.

```python
urlpatterns = [
   path('portfolios/', views.PortfolioListView.as_view(), name= 'portfolios'),
   path('portfolio/<int:pk>', views.PortfolioDetailView.as_view(), name='portfolio-detail'),
]
```

Finally, we create a template to render the portfolio details.

```html
{% extends 'portfolio_app/base_template.html' %}

{% block content %}
<!-- CSS Styles -->
<style>
  /* Defining a mouseover effect so the user can see the card they are interacting with easier*/
  .hover-card:hover {
    background-color: #f5f5f5;
  }
</style>

  <h1>{{ portfolio.title }}: {{ portfolio.student.name }} portfolio</h1>

  <p><strong>Portfolio Active:</strong> {{ portfolio.is_active }}</p>
  <p><strong>About:</strong> {{ portfolio.about }}</p>
  <p><strong>Contact Email:</strong> {{ portfolio.student.email }}</p>
  <!-- <a class="btn btn-primary" href="{% url 'update-portfolio' portfolio_id=portfolio.id %}" role="button">Update Portfolio</a> -->

  <h3>Project List:</h3>
  <a class="btn btn-primary" href="{% url 'create_project' portfolio.id %}" role="button">New</a>
  {% if projects %}
    {% for project in projects %}
    <div class="card hover-card">
      <div class="card-body">
        <h5 class="card-title">{{ project.title }}</h5>
        <a href="{{ project.get_absolute_url }}" class="btn btn-primary">View</a>
        <a href="{% url 'update-project' portfolio_id=portfolio.id project_id=project.id %}" class="btn btn-primary">Update</a>
        <a href="{% url 'delete-project' portfolio_id=portfolio.id project_id=project.id %}" class="btn btn-danger">Delete</a>
      </div>
    </div>
    {% endfor %}
  {% else %}
  <p>There are no projects.</p>
  {% endif %}
{% endblock %}
```

The above HTML has some other features to make the user experience more robust, what was done here will be discussed more in [Modifying User Interface in a Django Web App](#modifying-user-interface-in-a-django-web-app).

*Accreditation: Tyler Carroll & Matheus Abrantes*

#### More Explanations

**What are the CRUD actions and routes created so far?**

*Create, Update, and Delete Routes and Actions within urls.py.*

- Create Project: For adding a new project, we
  can define a URL pattern that maps to our createProject view.
  
  ```python
  path('project/create_project/', views.createProject, name='project-create'),
  ```

- Delete Project: To allow users to delete a project, we define a URL pattern that maps to our deleteProject view.
  
  ```python
  path('project/<int:pk>/delete_project/', views.deleteProject, name='project-delete'),
  ```

- Update Project: For updating a project, we map a URL to our updateProject view.
  
  ```python
  path('project/<int:pk>/update_project/', views.updateProject, name='project-update'),
  ```

- Update Portfolio: Updating a portfolio is done through the updatePortfolio view.
  
  ```python
  path('portfolio/<int:pk>/update_portfolio/', views.updatePortfolio, name='update-po
  ```

*In views.py*

- Create Project: In this view, we initiate a form for project creation. If the HTTP request method is `POST` and the form is valid, we save the new project and redirect the user to the relevant page.

- Delete Project: In the deleteProject view, we first get the project by its primary key. If the HTTP request method is `POST`, we delete the project and redirect the user to the portfolio detail page.

- Update Project: This view fetches the project by its ID. If the form is valid when we try to submit it, the project is updated.

- Update Portfolio: Similar to updating a project, we first fetch the portfolio. After validating the form, the portfolio is updated.

**How do you pass information from the database to display the active portfolios on the home page? Explore the Python shell command line to see what is returned for:**

```python
student_active_portfolios =
Student.objects.select_related('portfolio').all().filter(portfolio__is_active=True)
```

To ensure that only active portfolios are displayed on the home page, we can utilize Django's ORM capabilities to filter them out. This line of code fetches all student objects that have an associated active portfolio. The `select_related` method optimizes our query, reducing database hits when accessing related objects.

**Explore the code in index.html**

Django’s template system offers a way to define how to display data. Template tags and filters allow for dynamic generation of content and are enclosed in `{% %}` and `{{ }}`.

```python
<a class="btn btn-danger" href="{% url 'project-delete' pk=project.id %}" role="button">Delete</a>
```

This piece of code uses the URL template tag to generate the URL for the delete view dynamically. This is a powerful feature because it ensures that even if the URL patterns change, the links in templates will always remain correct.

*Accreditation: Matheus Abrantes*

### Implementing Forms in Django

In a web app, there are multiple scenarios where you would want to provide a user a form to fill out so you can store their data in the database. Django has a `forms` class to make this process easier to implement.

#### General Setup for Django Forms

When you want to have a user enter data in a form you have to create the form class, create the form in a template to be rendered, create a view to handle the HTTP requests (like POST) and add the view path to urls.py.

**Creating the form class:**

In Django, a model defines a table in the database and its members specify the columns of the table (like object title, object description, etc.). To allow the user to modify the database table via a form you must create a form that has the corresponding model’s members. In our project, we used Django’s ModelForm which can automatically generate certain fields based on what is defined in the `Meta` class.

The example below is placed in `forms.py`:

```python
class PortfolioForm(ModelForm):
    class Meta:
        model = Portfolio
        fields =('title', 'contact_email', 'is_active', 'about')
```

As a note, the fields defined in the `Meta` class must match the corresponding model’s members otherwise an error would occur. Since a `ModelForm` was used, the form elements (text fields/checkboxes) will be automatically created and rendered based on how the model’s members are defined.

**Creating a template to render the form:**

Since a `ModelForm` automatically renders the different fields in a template, creating a form template is very simple (see example below).

```html
<!-- inherit from base.html -->
{% extends 'portfolio_app/base_template.html' %}

{% block content %}

<form action="" method="POST">
 <h3>Updating {{ portfolio.title }}:</h3>

{% csrf_token %}
<table>
    {{ form.as_table }}
    </table>
    <input type="submit" name="Submit">
</form>

{% endblock %}
```

Here we use the HTML element `form` with the `POST` HTTP method since we want to update values in the database. The `{%csrf_token %}` part is for security purposes to prevent malicious attacks (hackers can inject a token to steal form data). Then, to render the form itself all you need is `<table> {{ form.as_table }} </table>`. Django will automatically render a form based on the model since we used `ModelForm`.

**Creating a view to handle the request:**

The view is called when the URL path is referenced in the template via the URL name. The view itself should specify the HTTP request method and perform operations to do work on the database. The view also should have render and redirect returns to handle what template is shown to the user and what shows up for the user after the request is processed.

Here is an example of the `updateProject` view:

```python
def updateProject(request, portfolio_id, project_id):
  project = get_object_or_404(Project, pk=project_id)
  portfolio = get_object_or_404(Portfolio, pk=portfolio_id)
  if request.method == 'POST':
    form = ProjectForm(request.POST, instance = project)
    if form.is_valid():
      form.save()
      return redirect('project-detail', pk=project_id)
  else:
    form = ProjectForm(instance=project)
    context={'form': form, 'portfolio': portfolio, 'project': project}
  return render(request, 'portfolio_app/project_update.html', context)
```

**Adding the path to `urls.py` to access the created view:**

To pull up the specific view when the user paths to the database operation, we specify the view in the URL path.

```python
path('portfolio/<int:portfolio_id>/update_project/<int:project_id>', views.updateProject, name='update-project'),
```

Note that the url path only mentions the view while a template references the path (see below).

```python
<a href="{% url 'update-project' portfolio_id=portfolio.id project_id=project.id %}" class="btn btn-primary">Update</a>
```

The above snip is found in `portfolio_detail.html` template and the URL name is referenced in the `href` attribute. When the button is clicked it references the url path to pull up the view which displays the `project_update.html` template.

*Accreditation: Tyler Carroll & Hasdi Ryan*

#### Creating Items via Forms

1. Create a blank form based on the defined `ModelForm` in `forms.py`.
   
   ```python
   form = ProjectForm()
   ```

2. Grab any relevant IDs so you can assign/relate them to a row (object) in the database.
   
   ```python
   portfolio = Portfolio.objects.get(pk=portfolio_id)
   ```

3. Handle the HTTP request while ensuring the form is valid.
   
   ```python
   if request.method == 'POST':
       # Create a new dictionary with form data and portfolio_id
       project_data = request.POST.copy()
       project_data['portfolio_id'] = portfolio_id
   
       form = ProjectForm(project_data)
       if form.is_valid():
   ```

4. Store the new object in memory without saving it to the database. We do this to make sure the data entered is valid and there was data entered.
   
   ```python
   project = form.save(commit=False)
   ```

5. Establish the relationship for the related models and save it to the database.
   
   ```python
   project.portfolio = portfolio
   project.save()
   ```

6. Ensure the relevant templates are rendered and the user is redirected to a page after submitting the form.
   
   ```python
   return redirect('portfolio-detail', portfolio_id)
   ```
   
   ```python
   context = {'form': form}
   return render(request, 'portfolio_app/project_form.html', context)
   ```

7. Create a template as seen in [General Setup for Django Forms](#general-setup-for-django-forms)

*Accreditation: Tyler Carroll & Hasdi Ryan*

#### Updating Items via Forms

1. Grab relevant private key IDs passed from the URL path. The get_object_or_404() method was used here so that it auto-handles the `DoesNotExist` error if an object does not exist in the database.
   
   ```python
   project = get_object_or_404(Project, pk=project_id)
   portfolio = get_object_or_404(Portfolio, pk=portfolio_id)
   ```

2. Fill the form with the existing data in the database by assigning the form instance to the variable containing the identification information.
   
   ```python
   form = ProjectForm(instance=project)
   ```

3. Handle the HTTP request while ensuring the form is valid. Specify that the request is associated with the instance of the item specified via the private key ID. 
   
   ```python
   form = ProjectForm(request.POST, instance = project)
   if form.is_valid():
   ```

4. Save the form.
   
   ```python
   form.save()
   ```

5. Ensure the relevant templates are rendered and the user is redirected to a page after submitting the form.
   
   ```python
   return redirect('project-detail', pk=project_id)
   ```
   
   ```python
   context={'form': form, 'portfolio': portfolio, 'project': project}
   return render(request, 'portfolio_app/project_update.html', context)
   ```

6. Create a template as seen in [General Setup for Django Forms](#general-setup-for-django-forms)

*Accreditation: Tyler Carroll & Hasdi Ryan*

#### Deleting Items via Forms

1. Grab relevant private key IDs passed from the URL path.
   
   ```python
   project = get_object_or_404(Project, pk=project_id)
   portfolio = get_object_or_404(Project, pk=portfolio_id)
   ```

2. Handle the HTTP request. As seen below, the `POST` method was used instead of `DELETE` since we could not get it working. However, using `POST` still works because we are processing the request in the database using `project.delete()`
   
   ```python
   if request.method == 'POST':
       project.delete()
   ```

3. Ensure the relevant templates are rendered and the user is redirected to a page after submitting the form.
   
   ```python
   return redirect('portfolio-detail', pk=project.portfolio.id)
   ```
   
   ```python
   context = {'project': project, 'portfolio':portfolio}
   return render(request, 'portfolio_app/project_delete.html', context)
   ```

4. The template for object deletion is different since it’s not a `ModelForm` like the create and update forms.
   
   ```python
   <!-- inherit from base.html -->
   {% extends 'portfolio_app/base_template.html' %}
   
   {% block content %}
   
   <form action="" method="POST">
    <p>Are you sure you want to delete "{{ project.title }}"?</p>
   
   {% csrf_token %}
   <a href="{% url 'portfolio-detail' pk=project.portfolio.id %}" class="btn btn-primary">Cancel</a>
   <input type="submit" name="Submit">
   </form>
   
   {% endblock %}
   ```

*Accreditation: Tyler Carroll & Hasdi Ryan*

### Deploying a Django Web App On Replit

***As a note:*** This part of the assignment had us working with Replit for about an hour. I had some issues with it and was not able to do it in that period of time, so I am going to provide the “step by step” process on how to do that and more information that I found on Replit as well. 

**Pre-Deployment Steps:**

- Preparing the Django project: We have to make sure that the project is ready for deployment (up to date).

- Replit account: If you don't have a Replit account, sign up at Replit.com.

**Steps Followed:**

- Set Up a Replit Account:
  
  - I linked my GitHub
  
  - Once registered, I verified my email and logged into the account.

- Create a New Replit:
  
  - Click on the `+ New Repl` button.
  
  - Choose `Python` as the language, and give your Repl a name.

***After setting up a new Replit, upload the Django project files. Replit provides a simple drag-and-drop interface.***

**Manage Dependencies:**

Even though I tried installing all the required packages for my Django project by using the requirements.txt file, I ran into some issues before they were imported from GitHub actually. Ideally, I would have run the command:

```bash
pip install -r requirements.txt
```

in the built-in terminal in Replit we need to install the necessary packages.

**Handle Environment Variables:**

To ensure that the project's sensitive information was not exposed, we should have moved Django `SECRET_KEY` and other sensitive data to Replit's secrets manager.

**Adjust Django Settings for Replit:**

**Adjust the Django settings for deployment:**

- Setting `DEBUG` to `False`.

- Configuring `ALLOWED_HOSTS` to include the Replit provided URL.

*Accreditation: Matthew Alter*

### Modifying User Interface In a Django Web App

Once the app is built and functioning correctly, consider adding styles and buttons to increase the user's experience.

#### Adding Buttons and Styling to Make Navigation Better

**Add a button on the project detail view to go back to the portfolio page like is available on the delete view. Also update the buttons to look the same.**

The code:

```html
{% extends 'portfolio_app/base_template.html' %}

{% block content %}
  <h1>Project Title: {{ project.title }}</h1>

  <p><strong>Description:</strong> {{ project.description }}</p>
  <p><strong>Portfolio:</strong> <a href="{{ project.portfolio.get_absolute_url }}">{{ project.portfolio }} </a></p>
  <a href="{% url 'portfolio-detail' pk=project.portfolio.id %}" class="btn btn-primary">Go Back</a>
{% endblock %}
```

What it looks like:

<img title="" src="file:///C:/Users/ty_ta/OneDrive/Desktop/Picture1.png" alt="" width="535" data-align="inline">

Clicking the button redirects the user to the portfolio_detail page.



**Update the Portfolio Projects to not use a list and use some grid, table, or card view.**

The code:

```html
{% extends 'portfolio_app/base_template.html' %}

{% block content %}
<!-- CSS Styles -->
<style>
  /* Defining a mouseover effect so the user can see the card they are interacting with easier*/
  .hover-card:hover {
    background-color: #f5f5f5;
  }
</style>

  <h1>{{ portfolio.title }}: {{ portfolio.student.name }} portfolio</h1>

  <p><strong>Portfolio Active:</strong> {{ portfolio.is_active }}</p>
  <p><strong>About:</strong> {{ portfolio.about }}</p>
  <p><strong>Contact Email:</strong> {{ portfolio.student.email }}</p>

  <h3>Project List:</h3>
  <a class="btn btn-primary" href="{% url 'create_project' portfolio.id %}" role="button">New</a>
  {% if projects %}
    {% for project in projects %}
    <div class="card hover-card">
      <div class="card-body">
        <h5 class="card-title">{{ project.title }}</h5>
        <a href="{{ project.get_absolute_url }}" class="btn btn-primary">View</a>
        <a href="{% url 'update-project' portfolio_id=portfolio.id project_id=project.id %}" class="btn btn-primary">Update</a>
        <a href="{% url 'delete-project' portfolio_id=portfolio.id project_id=project.id %}" class="btn btn-danger">Delete</a>
      </div>
    </div>
    {% endfor %}
  {% else %}
  <p>There are no projects.</p>
  {% endif %}
{% endblock %}
```

In the code above, I used bootstrap cards to separate the projects and their buttons. I also added a CSS class selector for a hover animation on the cards.

What it looks like:

<img src="file:///C:/Users/ty_ta/OneDrive/Desktop/Picture2.png" title="" alt="" width="556">

The "St1 Proj" card is currently being hovered over.

*Accreditation: Tyler Carroll*

#### Adding Dark Mode Functionality

I added a slider button to replace the normal button in the dark mode example. Then I changed some of the paragraphs and names. I tried adding a light mode title on the left of the slider and a dark mode title on the right. In short, you make the body class default black on white, then make a dark mode class reverse white on black. You then toggle the dark mode class with a slider button.

Code to enable dark mode:

```html
<!doctype html>
<html lang="en" data-bs-theme="dark">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Bootstrap demo</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN" crossorigin="anonymous">
  </head>
  <body>
    <h1>Hello, world!</h1>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL" crossorigin="anonymous"></script>
  </body>
</html>
```

To see how the slider button was made click [here]([How To Create a Toggle Switch](https://www.w3schools.com/howto/howto_css_switch.asp)).

*Accreditation: Hasdi Ryan*

### Resources

*Part 1*

- [Django Generic Display Views](https://docs.djangoproject.com/en/3.2/topics/class-based-views/generic-display/)

- [Django CRUD Example with Class Based Views](https://docs.djangoproject.com/en/3.2/intro/tutorial04/)

- [Django QuerySet API Reference](https://docs.djangoproject.com/en/3.2/ref/models/querysets/)

- [Django Built-in Template Tags and Filter](https://docs.djangoproject.com/en/3.2/ref/templates/builtins/)

*Part 2*

- [Models | Django documentation | Django](https://docs.djangoproject.com/en/4.2/topics/db/models/)

- [Extend your application · HonKit](https://tutorial.djangogirls.org/en/extend_your_application/ "https://tutorial.djangogirls.org/en/extend_your_application/")

- [Creating forms from models | Django documentation | Django](https://docs.djangoproject.com/en/4.2/topics/forms/modelforms/#:~:text=ModelForm%20is%20a%20regular%20Form,have%20already%20been%20defined%20declaratively).

- [What is CSRF token in Django?](https://www.tutorialspoint.com/what-is-csrf-token-in-django#:~:text=Django%20features%20a%20percent%20csrf,thus%20they%20are%20not%20executed).

- [http - POST vs PUT vs DELETE - Stack Overflow](https://stackoverflow.com/questions/48905762/post-vs-put-vs-delete)

- [Create Project with Portfolio](https://chat.openai.com/share/e5e5d2b2-58ed-4420-ab7c-0e79732a697b)

- [Django shortcut functions | Django documentation | Django](https://docs.djangoproject.com/en/4.2/topics/http/shortcuts/)

- [What is a 404 Error Code? What It Means and How to Fix It](https://www.techtarget.com/whatis/definition/404-status-code#:~:text=404%20and%20other%20response%20status,requested%20URL%20was%20not%20found)

- [How to Use *args and **kwargs in Python](https://www.freecodecamp.org/news/args-and-kwargs-in-python/#:~:text=**kwargs%20allows%20us%20to,denote%20this%20type%20of%20argument)

- [Making queries | Django documentation | Django](https://docs.djangoproject.com/en/4.2/topics/db/queries/)

*Part 3*

- https://docs.replit.com/repls/web-hosting

- [Security in Django | Django documentation | Django](https://docs.djangoproject.com/en/4.0/topics/security/)

*Part 4*

- [Cards · Bootstrap v5.0](https://getbootstrap.com/docs/5.0/components/card/)

- [Color modes · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/customize/color-modes/#:~:text=as%20shown%20below.-,Example,with%20the%20specified%20theme%20value)

- [How To Toggle Between Dark and Light Mode](https://www.w3schools.com/howto/howto_js_toggle_dark_mode.asp)

- [How To Create a Toggle Switch](https://www.w3schools.com/howto/howto_css_switch.asp)
