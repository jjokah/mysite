# My Blog site

A django blog site to share post and others...

## Table of Contents

- [Example](#example)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Features](#features)
- [Deployment](#deployment)

## Example

```python
def post_list(request, tag_slug=None):
    object_list = Post.published.all()
    tag = None

    if tag_slug:
        tag = get_object_or_404(Tag, slug=tag_slug)
        object_list = object_list.filter(tags__in=[tag])

    paginator = Paginator(object_list, 3)  # 3 posts in each page
    page = request.GET.get('page')
    try:
        posts = paginator.page(page)
    except PageNotAnInteger:
        # If page is not an integer deliver the first page
        posts = paginator.page(1)
    except EmptyPage:
        # If page is out of range deliver last page of results
        posts = paginator.page(paginator.num_pages)
    return render(request,
                  'blog/post/list.html',
                  {'page': page,
                   'posts': posts,
                   'tag': tag})
```

### Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

## Prerequisites

project that uses django rest api and react to create a todo list app

What things you need to install the software and how to install them

- Python 3
- Pip install packages

## Installation

To get a development env running:

> clone this repo to your local machine

```
git clone https://github.com/JohnJohnsonOkah/blog-site.git
```

> install requirements

```
pip install -r requirements.txt
```

> setup database

```
python manage.py migrate
```

> create superuser

```
python manage.py createsuperuser
```

> run development server

```
python manage.py runserver
```

... 👯 Now development server is up and running...
Go to http://127.0.0.1:8000/ to begin.

## Features

-

## Deployment

Additional notes about how to deploy this on a live system
