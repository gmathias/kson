# kson

Specification of a data format (and schema) designed for APIs, aiming to replace JSON.

The KSON schema can be used to describe JSON files.

# KSON

KSON tries solving all the issues of JSON:

## KSON pros
- 

JSON schema file using regex-like (*, +, [1-3]) syntax to express 

## KSON schema example

```javascript
/* description */
{
  /* comment */
  prop1: string,
  prop2: numeric,
  list1*: string
  list2+: {
    itemProp1: {}
    itemProp2?: string
  }
  listOfString: [string],
  listOfString2[]: string,
  yearDigits[2-4]: numeric,
  listOfObjects: [{
  }]
  prop3: {
    .?: string /* any key, optional, type string */
  },
  prop4: {
    .*: * /* 0 or N keys, any type each */
  },
  prop5: {
    .*: * /* 0 or N keys, any type each */
  },
  prop6: ** /* can be anything, any depth */,
  
  /* equivalent to 'prop7: *': */
  prop7,
  prop8: customType
  
  $types:{
    customType: numeric
  }
}
```

## Syntax

- `/**/` : comment

### keys
- `.` : a(ny) key
- `*` : 0 or N
- `+` : 1 or N
- `?` : optional (0 or 1)
- ``

### values
- (type) : json primitive type
- `**` : anything / any depth

# Examples

KSON:
```javascript
  prop1: string,
  prop2: numeric,
  list1*: string
  list2+: {
    itemProp1: {}
    itemProp2?: string
  }
  yearDigits: [2, 0, 1, 9]
}
```

# What's not?
- KSON is NOT JSON, i.e. can't be parsed by a JSON parser

# Why KSON?

## JSON pros & cons

### pros
- popularized because of JS front-ends
- quite intuitive syntax for Java/C programmers: {} = map/object, [] = list/array
- can be minified

### cons
- everything must be quoted
- loose primitive types: null, boolean, number, string (and object/array for structures).
- no comment possible inside JSON
- no (widely-used) schema (JSON schema is too verbose anyway)

## XML

### pros
- namespaces?

### cons
- verbose (repetition of start/end tags)

TODO
