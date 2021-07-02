# Urls and routing in Django 

## Tasks
1. So far we have created virtual environment inside 'django-exercise' folder and we have project named 'mysite'.  
   **After command ```ls -l``` you should have ```manage.py``` file on your list!  
    It means that you are inside 'mysite' project.  
    Don't forget to activate you virtualenv!**

2. Create app with name 'myapp':    
```python manage.py startapp myapp```  
- at this moment structure of folders and files in folder 'exercises-django' should look as follows:  
![ex2-1](../../../django-framework-exercises/screenshots/ex2-1.png)

3. Add information about your app to INSTALLED_APPS list in ```settings.py``` configuration file:  

   ![ex2-2](../../../django-framework-exercises/screenshots/ex2-2.png)

4. In ```views.py``` file of your ```myapp``` app create  function based view, that returns HttpResponse object. In the same file create  function based view, that returns JsonResponse object: 

   ![ex2-3](../../../django-framework-exercises/screenshots/ex2-3.png)

5. In your app (myapp) folder create file ```urls.py``` (app-level urls). Import previously created views and create two different paths (for both views, for example 'hello/' and 'json/'):    
   ![ex2-4](../../../django-framework-exercises/screenshots/ex2-4.png)

6. In your project (mysite) folder update ```urls.py``` file (project-level urls) by adding information about urls from your app. Use ```include()``` function:  
   ![ex2-5](../../../django-framework-exercises/screenshots/ex2-5.png)


7. Run development server:  
```python manage.py runserver```  

8. Open link ```http://127.0.0.1:8000/hello/``` in the browser. After URL of development server type path of your first URL from 'myapp/urls.py' (we have 'hello/' in this example). It works if you see the value returned in the first view:

   ![ex2-6](../../../django-framework-exercises/screenshots/ex2-6.png)  

9. Open link ```http://127.0.0.1:8000/json/``` in the browser. After URL of development server type path of your second URL from 'myapp/urls.py' (we have 'json/' in this example). It works if you see the value returned in the second view (in JSON format):

   ![ex2-7](../../../django-framework-exercises/screenshots/ex2-7.png) 

## Input/Output:
```
Working urls with proper views returning HttpResponse and JsonResponse objects.
```