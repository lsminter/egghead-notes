Instructor: 00:00 Right now, on the left-hand side of our screen, we have a huge query. It's collecting a bunch of data about customers and then about pets. GraphQL will let us do this. We can grab information about multiple types in one query, but I want to break this down into two separate queries, one of which will be for pets. The other will be for customers.

00:21 As soon as I break this down into two separate queries, we're going to run into an issue. When I click play, there are two unnamed queries.

If I click the second one of these, it says, "This anonymous operation must be the only defined operation." If there's more than one query in your query document, you're going to need to give both of these a name.

00:40 Right now, these are anonymous queries. Think of those like anonymous functions. We need to give them a name. I'll call the first one, "PetPage." I'll call the second one, "CustomerPage."

Now if I select the play button, we'll see the drop-down. We'll also see the operation name, so I can execute these queries one at a time.

01:00 Just to recap, whenever you have more than one query inside of a query document, you need to give it an operation name. The operation name can be whatever you want to call it but conventionally is capitalized.