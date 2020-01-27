Instructor: 00:00 Throughout this process, we've used the schema tab to look at all the available queries and types on this API. There's also a way that we can use the query language itself to look at, or introspect, the schema.

00:12 We're going to send some introspection queries to look at the schema for this API. The first thing we're going to query is __schema. This will show us the schema for this server. We can query all of the types on the types query, then let's look at the name, the kind, and the description.

00:32 I'm going to go ahead and click play on this, and we should see all of the different types.

Now, let's write a query for just the customer type. We're going to query __type. We're going to use the type name. Let's add Customer as a string.

00:50 Then we if want to find out what fields are available on the customer type, we can query fields, name, and description for each.

Now, if I look at customer, we see username, name, dateCreated, currentPets, all of the fields that we're familiar with, along with their descriptions.

01:09 What if we wanted to ask our schema which queries are available on this API? Let's write another query for AvailableQueries. We'll look at the schema, and then we'll look at queryType. Query type, we want to look at the fields, so what fields are available in that query type.

01:26 Then let's look at the name and the description.

We should see, if we click on AvailableQueries, totalPets, availablePets, checkedOutPets, all of the queries on this API.

The final query I want to send is for the pet interface.

01:41 Let's write a query for InterfaceTypes. We're going to look at __type. We'll look for the pet interface. Then we can look for the kind.

This will give us the kind, the interface. We're going to figure out the name, the description.

02:01 This should give us the pet and the description for that pet interface. Then finally, if you want to see all of the different implementations of that interface, all you need to do is look at possibleTypes. Then we'll query name, kind, description. There we go. Cat, Dog, Rabbit, and Stingray.