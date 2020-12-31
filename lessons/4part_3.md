Working on it..

    # Part 3 Practice - ROUND 2: Building a RESTful Api
    ## With Python, MongoDB, and Flask (Testing Environment coming soon...)
    Following this [tutorial](https://towardsdatascience.com/creating-a-beautiful-web-api-in-python-6415a40789af) from _Towards Data Science_, I want to understand how to build API's using these new technologies while still following an object-oriented design practice.

    **We are building a restaurant database where a user can signup, login, save user details, and have access to a list of favorited meals. We will also include an administrative track, where an admin can delete users and access any favorite meal list of a user.**


    ## Table of Contents
    1. [Understanding New Technologies](#understanding-new-technologies)
    1. [Setup](#setup)
    1. [Writing the Code](#writing-the-code)
    1. [Testing the Code](#testing-the-code)
    1. [Postman Confirmation](#postman-confirmation)
    1. [Bottom of Page](#bottom)

    ### Understanding New Technologies
    [Top of Page](#table-of-contents)
    #### What is a Web API?
    - API or Application Programming Interface is a way to present/expose data over the web. The typical formats we see out there are JSON (and XML). Personally, I have experience with JSON formatting (see [here](https://jsonapi.org) for the shared convention of presenting JSON).
    - Language you may hear:
      - "Endpoint" = It is the 'end' of a bit of communication; specific to API, an endpoint is the 'location' that a user/client/application can make a request and get a data response (where does the exposed data resource live? the api endpoint)
      - "Expose" = We hear expose a lot when programming. When we discuss databases or API's, we mean that we are providing the ability to access and manipulate the data (This word exists in multiple places in software, such as "exposing an object" - now we are providing the ability to access and manipulate the object)
      - "Request" = This is the act of "making the call". With API's, the request is making a call to the server (and the response is the formatted data). We can also see this word in use in other aspects of software. If I load google.com, I am making an HTTP request (aka, I'm making a call to googles server and the response is the website I see in my browser)
      - "Response" = This is what is returned back to a user. In API's, our response is the formatted data (the request is what started our process to get the response). Using the website analogy above, the HTTP Response would be the load of the google website in my browser)
      - "Routes" - Routes determine the structure of our API's and their endpoints. Working with computers, you've probably opened the File Directory/Manager (Mac: Finder, Windows: Windows/File Explorer). You might open up your user folder and then head further into documents and maybe you have another folder called Learn_Coding. Well, that URI (struggling with [URI vs URL](https://danielmiessler.com/study/difference-between-uri-url/)?) would be Priya/Documents/Learn_Coding. Well, let's look at an actual API URL:
      ![image](https://miro.medium.com/max/448/1*sauiWFwcEJPxiLlQZj_FYw.png)
        - The above breakdown is an API endpoint that exposes only Squirtles data
        - The "entry point" uses other language, such as namespace and
        - So we have a /pokemon route (if you hit this, you would expose all pokemon data)
        - Under that, we have another route /squirtle, this exposes just squirtle data
        - If I showed you this URL, what are the routes? `https://priyapower.com/api/v1/jobs/current_job`
    #### What is MongoDB?
    - MongoDB is a noSQL database that uses JSON formatting
      - uses a tree data structure
      - Uses documents
    - SQL vs noSQL
      - My resources ([Xplenty](https://www.xplenty.com/blog/the-sql-vs-nosql-difference/), [SoftwareTesting](https://www.softwaretestinghelp.com/sql-vs-nosql/))
      - Language you may hear:
        - "Database" = the location of information (data) records; gives access and manipulation ability; integrity and security can be built-into/handled-by the database
        - "Relational" = Regarding databases, this means it is structured with tables with pre-built relationships/dependencies
        - "Relationship" = In databases, we have three different [types of relationships](https://condor.depaul.edu/gandrus/240IT/accesspages/relationships.htm), one-to-one, one-to-many, and many-to-many. These, in essence, create ways to connect/relate/access the data. For example, a `Hobbes` (an instance of the Pet table) may "belong" to a `Calvin` (an instance of the Pet-Parent table). This means that the Pet-Parent "has" the Pet, and could potentially "have many" Pets, but Pets would only "belong" to 1 Pet-Parent. This is a one-to-many relationship. There is currently only a relationship between `Hobbes` and `Calvin`, however, `Calvin` can still get more pets, but `Hobbes` will always belong to ONLY `Calvin`, aka, `Suzy` isn't going to suddenly take ownership of `Calvin` (Want to understand my [pop-culture reference](https://i.pinimg.com/originals/64/a3/1b/64a31bd94c0dcade459aadebf199bec1.jpg)? See more [details](https://en.wikipedia.org/wiki/Calvin_and_Hobbes).)
        - "Schema" = the blueprint/organization of the data (how is the database constructed)
        - "Dynamic" = _________________________________________________________
        - "Static" =
        - "Field" =
      - SQL
        - SQL databases store information in tables and have relational abilities
        - Very rigid and structured (It's even in the name! Structure Query Language)
        - Has rules that define and manipulate the data
        - Has predefined schemas (aka [static schema](https://www.prisma.io/dataguide/intro/intro-to-schemas#static-vs-dynamic-schemas) structures)
        - Super widely-used
        - Database design, preparation, and organization is so important UP-FRONT
        - CONS: a change in the structure/database-design can be difficult to implement as well as cause errors/bugs/breaks in your system
        - SCALABILITY: vertically (single server, to increase performance, increase CPU, RAM, or SSD)
          - This means that SQL databases are preferred with small or consistent data sets
          - Because of its relational status - it also makes it preferred in multi-row transactions such as financial applications
      - NoSQL
        - No tables, instead you have doc, key:value, graph, and column
        - Dynamic schemas
        - Works with unstructured databases
        - Data can be stored in a multitude of ways:
          - Column-oriented - stores the data by serializing into columns; lets say we have a data record that has 3 bits of information, A, B, and C - our column will store column1=A, column2=B, column3=C
          - Document-oriented - these are typically JSON or XML; no schemas; each doc contains the data you want and is highly changeable; docs use key:value pairs (hashes)
          - Graph-based - has nodes and relationships; node = the noun (person, place, thing, object); relationships = the connection between 2 nodes; EXAMPLE: node1 = user, node2 = song, relationship = "favoriting the song"
          - Key:Value - stores data in pairs (key is the "caller" and the pair is the "return"); fast for writing, reading, and updating when you know the key; slow when you are making lots of changes or you access the entire data set
        - Super flexible
        - You can begin working without defining the structure of your database
        - Different parts of you system can have interaction with unique data structures instead of only relying on 1 defined data structure (use it how you need it!)
        - Syntax is varied in the different noSQL database world
        - You can update fields on the go
        - CONS: Lacks standardization and has less community support/documentation
        - SCALABILITY: horizontally (multi-servers for increase in performance)
          - This means that noSQL databases are preferred with large or ever-changing data sets
    #### What is Flask?
    -
    #### Flask vs Django
    -
    #### What is Postman?
    -
    ### Hosting that API - How?
    -


    ### Setup
    [Top of Page](#table-of-contents)
    ### Writing the Code
    [Top of Page](#table-of-contents)
    ### Postman Confirmation
    [Top of Page](#table-of-contents)
    ### Testing the Code
    [Top of Page](#table-of-contents)
    ###### Bottom
