# Dump GraphQL Queries to JSON

Parses GraphQL queries and exports the AST in JSON format.

## Usage

``` r
graphql2json(input, parse_schema = FALSE)
```

## Arguments

- input:

  a string with graphql syntax

- parse_schema:

  boolean to enable schema definition parsing

## Examples

``` r
graphql2json("{ field(complex: { a: { b: [ $var ] } }) }")
#> {"kind":"Document","loc":{"start": {"line": 1,"column":1}, "end": {"line":1,"column":43}},"definitions":[{"kind":"OperationDefinition","loc":{"start": {"line": 1,"column":1}, "end": {"line":1,"column":43}},"operation":"query","name":null,"variableDefinitions":null,"directives":null,"selectionSet":{"kind":"SelectionSet","loc":{"start": {"line": 1,"column":1}, "end": {"line":1,"column":43}},"selections":[{"kind":"Field","loc":{"start": {"line": 1,"column":3}, "end": {"line":1,"column":41}},"alias":null,"name":{"kind":"Name","loc":{"start": {"line": 1,"column":3}, "end": {"line":1,"column":8}},"value":"field"},"arguments":[{"kind":"Argument","loc":{"start": {"line": 1,"column":9}, "end": {"line":1,"column":40}},"name":{"kind":"Name","loc":{"start": {"line": 1,"column":9}, "end": {"line":1,"column":16}},"value":"complex"},"value":{"kind":"ObjectValue","loc":{"start": {"line": 1,"column":18}, "end": {"line":1,"column":40}},"fields":[{"kind":"ObjectField","loc":{"start": {"line": 1,"column":20}, "end": {"line":1,"column":38}},"name":{"kind":"Name","loc":{"start": {"line": 1,"column":20}, "end": {"line":1,"column":21}},"value":"a"},"value":{"kind":"ObjectValue","loc":{"start": {"line": 1,"column":23}, "end": {"line":1,"column":38}},"fields":[{"kind":"ObjectField","loc":{"start": {"line": 1,"column":25}, "end": {"line":1,"column":36}},"name":{"kind":"Name","loc":{"start": {"line": 1,"column":25}, "end": {"line":1,"column":26}},"value":"b"},"value":{"kind":"ListValue","loc":{"start": {"line": 1,"column":28}, "end": {"line":1,"column":36}},"values":[{"kind":"Variable","loc":{"start": {"line": 1,"column":30}, "end": {"line":1,"column":34}},"name":{"kind":"Name","loc":{"start": {"line": 1,"column":30}, "end": {"line":1,"column":34}},"value":"var"}}]}}]}}]}}],"directives":null,"selectionSet":null}]}}]} 
graphql2json("schema { query: QueryType }", TRUE)
#> {"kind":"Document","loc":{"start": {"line": 1,"column":1}, "end": {"line":1,"column":28}},"definitions":[{"kind":"SchemaDefinition","loc":{"start": {"line": 1,"column":1}, "end": {"line":1,"column":28}},"directives":null,"operationTypes":[{"kind":"OperationTypeDefinition","loc":{"start": {"line": 1,"column":10}, "end": {"line":1,"column":26}},"operation":"query","type":{"kind":"NamedType","loc":{"start": {"line": 1,"column":17}, "end": {"line":1,"column":26}},"name":{"kind":"Name","loc":{"start": {"line": 1,"column":17}, "end": {"line":1,"column":26}},"value":"QueryType"}}}]}]} 
```
