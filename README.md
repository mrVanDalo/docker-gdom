
# DOM Traversing and Scraping using GraphQL

* [Example server](http://gdom.graphene-python.org/)
* [Github Project](https://github.com/syrusakbary/gdom)

GDOM is the next generation of web-parsing, powered by GraphQL syntax and the Graphene framework.


# Run


    docker run -p 8080:8080 mrVanDalo/gdom
    

now have a look at [localhost](http://localhost:8080/)


## Example Queries

You find some [Examples on the project page](https://github.com/syrusakbary/gdom/tree/master/examples).
Here are some of mine:


    ;;; -*- mode: restclient; -*-
    
    #
    # classicprogrammingpaintings.com example
    #
    POST http://localhost:8080/graphql
    Content-Type: application/graphql
    
    {
      page(url:"http://classicprogrammerpaintings.com") {
        items: query(selector:"article.photo") {
          title: text(selector:"p:eq(0)")     
          artist: text(selector:"p:eq(1)")
          image: attr(selector:"img", name:"src")
        }
      }
    }


# Build

As usual:

    docker build -t gdom .
