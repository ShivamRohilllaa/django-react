Connect React js with django
Method 1) 
Make a django project and make an virtual enviornment and activate that enviornment.
Install djangorestframework
INSTALLED_APPS = [
     
    'rest_framework',
    'frontend',
]

Create react app
npx create-react-app frontend
and run that npm run build

Settings.py
'DIRS': [os.path.join(BASE_DIR, '../frontend')],

STATICFILES_DIRS = [
    os.path.join(BASE_DIR, '../frontend/build/static'),
]

python manage.py runserver

Method 2)
django-cors-headers

INSTALLED_APPS = [
    'rest_framework',
    'corsheaders', # new

]


MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware', # new
    'django.middleware.common.CommonMiddleware', # new

]

CORS_ORIGIN_WHITELIST = (
    'localhost:3000/'
)

http-common.js

import axios from "axios";

export default axios.create({
  baseURL: "http://localhost:8080/api",
  headers: {
    "Content-type": "application/json"
  }
}); 