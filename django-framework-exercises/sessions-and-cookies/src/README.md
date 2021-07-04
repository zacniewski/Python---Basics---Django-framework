# Sessions and cookies in Django  

## Tasks
1. So far we have created virtual environment inside 'django-exercise' folder and we have project named 'mysite' with app named 'myapp'.  
*  App handles few urls, and each url allows user for calling specific view.  
*  Views return response objects (HttpRespons or JsonResponse) with hardcoded values or convenient functions for both function based views (FBV) and class based views (CBV) are used. 
* Templates, template tags and variables, template extending work in appropriate way.

*  **Don't forget to activate you virtualenv!**  

2. Session availability in Django.
*  Check if you have session functionality available in your project: in ```settings.py``` configuration file you should have  ```django.contrib.sessions.middleware.SessionMiddleware``` specified in the MIDDLEWARE list.
* to store session information in a Django model/database (will be covered later) the most straightforward approach is to use the ```django.contrib.sessions``` application (check the INSTALLED_APPS list).

   ![ex4-1](../../../django-framework-exercises/screenshots/ex4-1.png)  

2. Working with cookies 
* our database ```db.sqlite3``` is empty and without tables. In order to work with sessions (and many other things) in Django we must create proper tables. Luckily, Django will do it for us using ORM (Object-Relational Mapping) and 'migrations' (this topics will be covered later). If you don't do it, you can encounter errors like this:  
      ![ex4-2](../../../django-framework-exercises/screenshots/ex4-2.png)

* to do this, simply stop development server and run command: ```python manage.py migrate```.      
      ![ex4-3](../../../django-framework-exercises/screenshots/ex4-3.png)
* after proper execution of this command you shouldn't see warnings about migrations mentioned earlier. 

* check if your browser supports cookies by modifying [example](https://docs.djangoproject.com/en/3.2/topics/http/sessions/#setting-test-cookies) from documentation:
   * add view ```set_test_cookie```, that uses built-in function with the same name and don't forget to return HttpResponse in this view!
      ![ex4-4](../../../django-framework-exercises/screenshots/ex4-4.png)
   * add url ```set-test-cookie``` for this view in app-level ```urls.py``` and remember about importing this view earlier!
      ![ex4-5](../../../django-framework-exercises/screenshots/ex4-5.png)
   * in browser open link ```http://127.0.0.1:8000/set-test-cookie/``` to set the testing cookie,
   * add view ```check_test_cookie``` that uses ```test_cookie_worked()``` function and ```delete_test_cookie()``` function.
      ![ex4-6](../../../django-framework-exercises/screenshots/ex4-6.png)
   * add url ```check-test-cookie``` for this view in app-level ```urls.py``` and remember about importing this view earlier!
         ![ex4-7](../../../django-framework-exercises/screenshots/ex4-7.png)
   * in browser open link ```http://127.0.0.1:8000/check-test-cookie/``` to check the testing cookie,
         ![ex4-8](../../../django-framework-exercises/screenshots/ex4-8.png)

3. Managing your own cookies.
* documentation about [setting own cookies](https://docs.djangoproject.com/en/3.2/ref/request-response/#methods) in Django (scroll to ```set_cookie()``` method),

* Django’s request object has an attribute COOKIES (available via ```request.COOKIES```), which behaves like standard dictionary. You can  use dictionary's methods like for example [get](https://www.geeksforgeeks.org/get-method-dictionaries-python/),  

* add view ```set_own_cookie``` that checks if we have set cookie named ```visits```:
   * if yes then increase (+1) value for this cookie and set value ```Hello again``` for second cookie named ```text```.  
   * if not set value of this cookie on 1 and set value ```Welcome for the first time``` for second cookie named ```text```
      ![ex4-9](../../../django-framework-exercises/screenshots/ex4-9.png)

* Hint: cookie's values are always strings, so remember about casting!
* add url ```set-own-cookie``` for this view in app-level ```urls.py``` and remember about importing this view earlier!
         ![ex4-10](../../../django-framework-exercises/screenshots/ex4-10.png)
* in browser open link ```http://127.0.0.1:8000/set-own-cookie/``` to check setting cookies,  and open 'Storage' tab in browser's Web Development Tools
         ![ex4-11](../../../django-framework-exercises/screenshots/ex4-11.png)
* Values of cookies ```visits``` and ```text``` clearly inform us about first visit on this page. But after another visits, the values of cookies are different:
         ![ex4-12](../../../django-framework-exercises/screenshots/ex4-12.png)


* The ```sessionid``` cookie contains a series of letters and numbers which Django uses to uniquely identify your session. From there, all your session details can be accessed - but only on the server side. Django uses this cookie to look up the session in the database where it stores all the server side cookies about that session.

4. Reading and writing session data.  
* more secure way to save session information is to store any such data on the server side. We can then use the ```sessionid``` cookie which is stored on the client side (but is effectively anonymous) as the key to unlock the data.

* a ```sessionid``` cookie is still used to remember the client’s machine (so technically a browser side cookie exists), however all the data is stored server side.

* a Django request object has a ```session``` attribute that acts like a dictionary.

* add view ```create_session``` that creates session variables - ```name```, ```surname``` and ```password``` (hard-coded values):
      ![ex4-13](../../../django-framework-exercises/screenshots/ex4-13.png)

* add url ```create-session``` for this view in app-level ```urls.py``` and remember about importing this view earlier!
         ![ex4-13](../../../django-framework-exercises/screenshots/ex4-13.png)

* in browser open link ```http://127.0.0.1:8000/create-session/``` to set session data.

* add view ```read_session``` that reads created variables.
      ![ex4-14](../../../django-framework-exercises/screenshots/ex4-14.png)

* add url ```read-session``` for this view in app-level ```urls.py``` and remember about importing this view earlier!
         ![ex4-15](../../../django-framework-exercises/screenshots/ex4-15.png)

* in browser open link ```http://127.0.0.1:8000/read-session/``` to read your session data.
         ![ex4-16](../../../django-framework-exercises/screenshots/ex4-16.png)

* add view ```delete_session``` that deletes created variables.
      ![ex4-17](../../../django-framework-exercises/screenshots/ex4-17.png)

* add url ```delete-session``` for this view in app-level ```urls.py``` and remember about importing this view earlier!
      ![ex4-18](../../../django-framework-exercises/screenshots/ex4-18.png)

* in browser open link ```http://127.0.0.1:8000/delete-session/``` to delete your session data.
         ![ex4-19](../../../django-framework-exercises/screenshots/ex4-19.png)

* in browser open link ```http://127.0.0.1:8000/read-session/``` to read your current session data.
         ![ex4-20](../../../django-framework-exercises/screenshots/ex4-20.png)

## Input/Output:
```
Working with cookies (testing browser support, setting own) and session management (writing, reading and deleting).
```