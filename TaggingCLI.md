# Tagging CLI

STILL UNDER DEVELOPMENT

## Definitions
### Tag
A *tag* is a category (semantic dimension in a manner) that denotes some *resource* (some code feature in our case).

### Resource
*Resource* in *Soft Spider* space are usually http-reference to project repository that contain some prototypical code.
Such *resources* are marked with *tag sets*.

### Tag set
*Tag sets* as usual are used to mark *resources*, as well as in *queries*.  
Textual representations of tag sets use spaces as separators.

## Marking
```sh
resource: tag-1 tag-2 ... tag-n 
```

## Queries
*Queries* are used for getting *resources*.

### Tag sets in queries
Textual representation of *tag sets* in *queries* are used in the same way as when marking:
```sh
tag-1 tag-2 ... tag-n 
```

Relevant resources are those that are marked with a tag set, that includes the query tag set.  
Suppose there are resources:
 
https://github.com/softspider/styled-components: react styled-components    
https://github.com/softspider/cra-redux-thunk: react redux redux-thunk    
https://github.com/softspider/redux: redux state-management  

Then, having a query

```sh
react redux 
```

as a result we'll get:

~~~~
https://github.com/softspider/cra-redux-thunk
~~~~
  
### Subspace queries
A colon after a set of tags means a request to receive in a some sense a semantic subspace - only those
resources that were marked with the specified tag set and with its subsets (but no more).

```sh
tag-1 tag-2 ... tag-n:
```

Suppose there are resources:
 
https://github.com/softspider/typeorm: typescript backend graphql      
https://github.com/softspider/ts-backend: typescript backend  
https://github.com/softspider/ts: typescript    
https://github.com/softspider/backend: backend      

Then, having a query

```sh
typescript backend:
```

we'll get:

~~~~
https://github.com/softspider/ts-backend     
https://github.com/softspider/ts
https://github.com/softspider/backend    
~~~~

*Subspace queries* are useful in order to avoid unnecessary features and accompanying excessive boilerplate code in
obtaining prototypes. 

Having a given subspace, you can already select the necessary sections in it, for example:

Having a query

```sh
typescript backend: backend
```

we'll get code in '*typescript backend*' subspace with *backend* only:

~~~~
https://github.com/softspider/backend    
~~~~

And having a query:

```sh
typescript backend: typescript
```

we'll get code in '*typescript backend*' subspace with *typescript* only:

~~~~
https://github.com/softspider/ts
~~~~

In other words, there are no result code resources with graphql in both cases.


## Tag glossary 
All tags used are contained in the glossary - an alphabetical list of tags with their
definitions and/or explanations.
