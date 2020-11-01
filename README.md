# Quarkus Reproducer for JsonNode serialization issue

This example is not functional and is meant to reproduce Issue https://github.com/quarkusio/quarkus/issues/12776

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
Array : false ,
bigDecimal : false ,
bigInteger : false ,
binär : falsch ,
Boolescher Wert : false ,
containerNode : true ,
double : false ,
float : false ,
floatPointNumber : false ,
int : false ,
IntegralNumber : false ,
lang : falsch ,
missingNode : false ,
null : false ,
Nummer : falsch ,
pojo : falsch ,
kurz : falsch ,
Text : falsch ,
valueNode : false ,
leer : falsch ,
nodeType : "OBJECT" ,
Objekt : wahr ,
}}

````