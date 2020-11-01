# Quarkus Reproducer for JsonNode serialization issue

This example is not functional and is meant to reproduce Issue https://github.com/quarkusio/quarkus/issues/13043

#### Version

* Quarkus 1.9.1.Final

#### Issue

Calling the endpoint at http://localhost:8080/hello/test

````
    @GET
    @Path("/test")
    public Response get() throws JsonProcessingException {
        ObjectMapper mapper = new ObjectMapper();
        JsonNode json = mapper.readTree("{\"id\": \"132\", \"name\": \"Alice\"}");
        return Response.accepted(json).build();
    }
````

produces not the expected JSON string as a result, but instead

````

{
array: false,
bigDecimal: false,
bigInteger: false,
binary: false,
boolean: false,
containerNode: true,
double: false,
float: false,
floatingPointNumber: false,
int: false,
integralNumber: false,
long: false,
missingNode: false,
null: false,
number: false,
pojo: false,
short: false,
textual: false,
valueNode: false,
empty: false,
nodeType: "OBJECT",
object: true,
}

````