
# Table of Contents

<<<<<<< HEAD
1.  [Planification for current Sprint](#org71edfcd) - Quim
2.  [Requirements - Product](#org9935dda) - Emina & Jass
3.  [Main use cases](#orge7ab8cc) - Emina & Jass
4.  [General architecture](#orgfde3214) - Quim & Sergi
5.  [Database model](#org9739469) - Sergi
    1.  [Users model](#org9a18c0b)
    2.  [Enterprise Module](#orgcfa15d1)
    3.  [Product Module](#org1d0ee40)
    4.  [Formal Offer module](#org29d0d47)
        1.  [We didn&rsquo;t make any notes for the products](#orgcfe654e)
6.  [Web application](#orgda444e6) - Sergi
    1.  [Authentication](#org8d3dfe4)
7.  [Financial Factors](#orgf7f9ad1) - Oriol & Nico
=======
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
>>>>>>> 28220e3069e894d8f5dc691d11b329cccd70301f



<a id="orge067dbe"></a>

# Planification for current Sprint

Tasks

-   Sprint backlog
-   Dedication time to each one (an estimation)
-   Indicator related to evolution between Sprints. Concretely, if there
    is some change it should be specified


<a id="org53b1ef4"></a>

# Requirements - Product

Tasks

-   The current list of requirements should be well defined and well explained for any participant.
-   Indicator related to evolution between Sprints. Concretely, if there is some change, for example new requirements or modification inside an existing one, it should be specified.


<a id="orgdd37f50"></a>

# Main use cases

Tasks

-   List
-   Reason to be essential
-   Indicator related to evolution between Sprints. Concretely, if there is some change it should be specified.


<a id="org1b1e749"></a>

# General architecture

Tasks

-   Definition (relational diagram, image, etc.)
-   Explanation
-   Decisions taken
-   Indicator related to evolution between Sprints. Concretely, if there is some change it should be specified.


<a id="orgee1603c"></a>

# Database model

The database model can be looked on at the figure [18](#org0456258). In the following sections, it will be discussed in a module to module basis why and how they are done.

![img](img/database-model.png "UML diagram for the database.")


<a id="orgb53ba2b"></a>

## Users model

The users model is already provided by Django framework. Its purpose is to be able to store the usernames and password in a secure way. It was only needed to do the operations needed for the authentication and not the CRUD operations on the User, based on a JWT bearers shcema. In [6.1](#orgf09fb3a) it will be explained fully on detail about how we did the authentication process.


<a id="org79e9ed8"></a>

## Enterprise Module

We wanted to have a separated table of the user with the data that we need from the enterprises to work properly. It is a well known practice to separate the user specific fields in another table instead of extending the User model. In this way, we can use 3rd party apps that are well tested for authentication and authorization.


<a id="orgf4f8584"></a>

## Product Module

Each enterprise can post a number of products depending on the plans that they have subscribed. This module models the necessary data that should be stored to do the database.

For the searcher endpoint it will be needed a way to categorize the product. For this, it will be used Spacy, which lets us extract keywords and match against more general tags. For example, it can categorize &ldquo;apple&rdquo; as &ldquo;fruit&rdquo;. Then, when a client wants to search for a &ldquo;pear&rdquo;, instead of searching against the whole database, it will only search on the &ldquo;fruit&rdquo; tag.


<a id="org7d11f74"></a>

## Formal Offer module

In this module we will have the models that serve the purpose to create the formal offer. The most important model is the FormalOffer, which contains the necessary information to create the unsigned PDF, as well as the current PDF. It iterates with different versions between the enterprise that offers the service and the one that has solicited them, sending them through the chat. At the end, the signed PDF will be agreed upon and signed by both enterprises.


<a id="orgb3bd3b7"></a>

### TODO We didn&rsquo;t make any notes for the products

-   Plantuml diagram
-   The purpose of each model
-   Decisions taken
    -   Why we did tag as we did.
-   The last one is for the other sprints.

Tasks

-   Definition (for example: relational diagram)
-   Explanation
-   Decisions taken
-   Indicator related to evolution between Sprints. Concretely, if there is some change, for example new requirements or modification inside an existing one, it should be specified.


<a id="orgb83efd8"></a>

# Web application


<a id="orgf09fb3a"></a>

## Authentication

Tasks
  Main screens.

-   Relations
-   Decisions taken


<a id="org448d13b"></a>

# Financial Factors

Tasks

-   Cash flow (ideally, 4 years) by quarters or months. In relation with the Sprint 1, it implies summarize the work done during Sprint 1.
-   Flow chart. It should show when the cash flow will be positive for the first time that is, you will not need borrowed money.
-   To calculate payback and annual ROI with NPV, IRR and BEP.
-   It is needed to offer explanations to the previous points.
-   If you perfume the previous points of financial factors by scenarios (optimistic, normal, and pessimistic), it will be valued as extra work.
-   Indicator related to evolution between Sprints. Concretely, if there are some changes it should be specified.

