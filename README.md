# Very Best Auth

In this project, we'll practice allowing users to sign in and customizing the content of the application for them.

## Problem Statement

I always forget which restaurant serves my favorite ramen, sushi, or burger in the city. Also, I don't even know which dishes I ought to be trying to find a favorite spot for.

## Pitch

Very Best allows you to "bookmark" your favorite venue for each of 100 dishes that we think you ought to form an opinion about.

# Domain Model

The central model in this application will be **Favorite**. This is what a user creates when they love some restaurant's rendition of a dish. The favorites table will look like this:

```yaml
favorite:
  user_id:integer
  dish_id:integer
  venue_id:integer
  notes:text
```

Notice all of the foreign keys. The supporting cast of models will be:

```yaml
cuisine:
  name:string

dish:
  name:string
  cuisine_id:integer

neighborhood:
  name:string
  city:string

venue:
  name:string
  address:string
  neighborhood_id:integer
```

And also users, but we'll use a new technique to create users. For now, let's generate the above using [starter_generators](https://gist.github.com/rbetina/80d3cf2cf82666ed1c0f).

Next, go through each model and add all **one-to-many associations**. An easy way to do this: look for foreign keys -- anywhere you see a foreign key, that model gets a `belongs_to`. The other model gets a `has_many`.

Next, go through and add any **many-to-many assocations** that make sense.

Next, go through each model and add any **validations** that make sense for each column. Usually, these are either *presence* or *uniqueness* rules.

Next, we'll talk about adding user accounts with [Devise](https://github.com/plataformatec/devise).
