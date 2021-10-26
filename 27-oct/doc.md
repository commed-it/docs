
# Table of Contents

1.  [Planification for current Sprint](#orge067dbe)
2.  [Requirements - Product](#org53b1ef4)
3.  [Main use cases](#orgdd37f50)
4.  [General architecture](#org1b1e749)
5.  [Database model](#orgee1603c)
    1.  [Users model](#orgb53ba2b)
    2.  [Enterprise Module](#org79e9ed8)
    3.  [Product Module](#orgf4f8584)
    4.  [Formal Offer module](#org7d11f74)
        1.  [We didn&rsquo;t make any notes for the products](#orgb3bd3b7)
6.  [Web application](#orgb83efd8)
    1.  [Authentication](#orgf09fb3a)
7.  [Financial Factors](#org448d13b)

<a id="org039a74e"></a>

# Planification for current Sprint

Tasks

-   Sprint backlog
-   Dedication time to each one (an estimation)
-   Indicator related to evolution between Sprints. Concretely, if there
    is some change it should be specified


<a id="org30e4382"></a>

# Requirements - Product

Tasks

-   The current list of requirements should be well defined and well explained for any participant.
-   Indicator related to evolution between Sprints. Concretely, if there is some change, for example new requirements or modification inside an existing one, it should be specified.


<a id="orgc47d17e"></a>

# Main use cases

Tasks

-   List
-   Reason to be essential
-   Indicator related to evolution between Sprints. Concretely, if there is some change it should be specified.


<a id="org0c10ad2"></a>

# General architecture

Tasks

-   Definition (relational diagram, image, etc.)
-   Explanation
-   Decisions taken
-   Indicator related to evolution between Sprints. Concretely, if there is some change it should be specified.


<a id="org03a016d"></a>

# Database model
The database model can be looked on at the figure [1](img). In the following sections, it will be discussed in a module to module basis which purpose do they serve and which models do they have to achieve that.

![img](img/database-model.png "UML diagram for the database.")


<a id="org71bfb5a"></a>

## Users model

The users model is already provided by Django framework. Its purpose is to be able to store the usernames and password in a secure way. It was only needed to do the operations needed for the authentication and not the CRUD operations on the User, based on a JWT bearers shcema. In [6.1](#org712facd) it will be explained fully on detail about how we did the authentication process.

<a id="org7015789"></a>

## Enterprise Module

It is a well known practice, inside the Django framework, to separate the user specific fields in another table instead of extending the User model. In this way, 3rd party apps can be used, for example for the authentication part. With this method, not only such information as the name, the contact, or their description can be stored for a specific user, but also 3rd party apps that operate on the user can still be used.


<a id="org2e942e4"></a>

## Product Module

Each enterprise can post a number of products depending on the plans that they have subscribed. This module models the necessary data that should be stored to do the database.

For the searcher endpoint it will be needed a way to categorize the product. For this, it will be used Spacy, which lets us extract keywords and match against more general tags. For example, it can categorize &ldquo;apple&rdquo; as &ldquo;fruit&rdquo;. Then, when a client wants to search for a &ldquo;pear&rdquo;, instead of searching against the whole database, it will only search on the &ldquo;fruit&rdquo; tag.

To achieve this purpose, we store the tags that are currently used in a table, and we have a many to many relationship between the Product and Tag table. We made a table for the Tag instead of an enumaration as the Tag table will be increased programatically when it encounters a new tag that does not relate to anything at all.

In the near future, and, given the fact that the clients won&rsquo;t know about this inside feature, we will rearrenge the tags to minimize the distance and provide a better suport.

<a id="orgd5e0a34"></a>

## Formal Offer module

In this module we will have the models that serve the purpose to create the formal offer. The most important model is the FormalOffer, which contains the necessary information to create the unsigned PDF, as well as the current PDF. It iterates with different versions between the enterprise that offers the service and the one that has solicited them, sending them through the chat. At the end, the signed PDF will be agreed upon and signed by both enterprises.

Upon generating the requirements of the FormalOffer, it was said that it could be provided the different contracts that have been made with the same product, as in most cases, they will be similar.

The problem was that when the clients start their chat they have some time to discuss how and what should be done in the formal offer in a period of time. For this reason, it was decided that creating a model that has a chat related to them and the product would be better than storing it in a FormalOffer that all the other values are Null. With this solution in mind, the Encounter model was created.

<a id="orgc6dbfff"></a>
# Web application

Tasks
  Main screens.

-   Relations
-   Decisions taken




<a id="org712facd"></a>

## Authentication
The problem was solved by using two well known apps in the Django community. The first is mantained by an Enterprise called *IntenCT* who specilizes on doing web applications using Django. This enterprise published a library that provides an authentication system. It specializes on keeping users that come from different apps, while proving a solution for this based on tokens. With this, implementing simple JavaScript Web Tokens are just a step on the configuration, but also adding a way to integrate other services for authentication, as a **Log In with Google** button use case.

The other app that is used provides a REST entrypoint for the first one. In this way, with just a small configuration a ready-to-go service is achieved. 

<a id="orga29bc04"></a>

# Financial Factors

Tasks

-   Cash flow (ideally, 4 years) by quarters or months. In relation with the Sprint 1, it implies summarize the work done during Sprint 1.
-   Flow chart. It should show when the cash flow will be positive for the first time that is, you will not need borrowed money.
-   To calculate payback and annual ROI with NPV, IRR and BEP.
-   It is needed to offer explanations to the previous points.
-   If you perfume the previous points of financial factors by scenarios (optimistic, normal, and pessimistic), it will be valued as extra work.
-   Indicator related to evolution between Sprints. Concretely, if there are some changes it should be specified.

