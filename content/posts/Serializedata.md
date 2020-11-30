---
title: Serialize Data in Django
date: "2020-08-19"
template: "post"
draft: false
slug: "serilize"
category: "Programming"
tags:
  - "Python"
  - Django
  - "Programming"
description: "Serialize your json using django rest framework"
socialImage: "/media/42-line-bible.jpg"
---
### Serialize data using DRF

Make sure you install Django rest framework in your virtual environment.

For reference look at my [repo](https://github.com/kumaraswins/django).

In the `view.py`

```python
class CompanyViewSet(viewsets.ModelViewSet):
    queryset = models.Company.objects.all()
    serializer_class = serializers.CompanySerializer
```

Create a file [`serializers.py](http://serializers.py)` in the same folder of the views, you can specify the fields in the model in the fields tuple.

```python
# Serializers part
    from rest_framework import serializers
    from rest_framework import authentication as auth
    from rest_framework import permissions as perm
    from . import models
    from project.users.models import User
    from django.conf import settings
    
    class CompanySerializer(serializers.ModelSerializer):
        class Meta:
            model = models.Company
            fields = ('id', 'name', 'location',)
```

Serialize data and send all the fields 

```python
   class CompanySerializer(serializers.ModelSerializer):
        class Meta:
            model = models.Company
            fields = '__all__'
```

Exclude fields while serializing

```python
class CompanySerializer(serializers.ModelSerializer):
    class Meta:
        model = Account
        exclude = ['users']
```

Customize the fields before sending

```python
class OptionsSerializer(serializers.ModelSerializer): 
    image_url = serializers.SerializerMethodField() # defining custom method
    class Meta:
        model = models.Options
        fields = ('image_url','title',)

    def get_image_url(self, obj):
        return obj.modelname # your logic here
```

Serialize multiple data, by default it is a single object, if you want an array mention `many=True`

```python
queryset = Book.objects.all()
serializer = BookSerializer(queryset, many=True)
serializer.data
```