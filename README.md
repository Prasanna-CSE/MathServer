# Ex.05 Design a Website for Server Side Processing
## Date:01/04/24

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
## math.html

<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of Surface</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
    background-color: red;
}
.edge {
    width: 100%;
    padding-top: 250px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick dashed rgb(232, 234, 107);
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: blue;
}
.formelt {
    color: black;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h1 {
    color: red;
    padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>Surface area of Rigth cylinder</h1>
        <h3>PRASANNA L (212221040130)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Radius: <input type="text" name="radius" value="{{r}}">m<br/>
            </div>
            <div class="formelt">
                Height: <input type="text" name="height" value="{{h}}">m<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"><br/>
            </div>
            <div class="formelt">
                Area: <input type="text" name="area" value="{{area}}">m<sup>2</sup><br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>

## views.py


from django.shortcuts import render
def rectarea(request):
    context={}
    context['area'] = "0"
    context['b'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        b = request.POST.get('base','0')
        h = request.POST.get('height','0')
        print('request=',request)
        print('Base=',b)
        print('Height=',h)
        area = (int(b) * int(h))
        context['area'] = area
        context['b'] = b
        context['h'] = h
        print('Area=',area)
    return render(request,'mathapp/math.html',context) 

## urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofsurface/',views.surfacearea,name="areaofsurface"),
    path('',views.surfacearea,name="areaofsurfaceroot")
]

```
## SERVER SIDE PROCESSING:
![alt text](<Screenshot (106).png>)
## HOMEPAGE:
![alt text](<Screenshot (105).png>)
## RESULT:
The program for performing server side processing is completed successfully.
