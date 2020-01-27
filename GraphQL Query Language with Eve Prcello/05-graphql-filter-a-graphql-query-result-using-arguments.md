Instructor: 00:00 So far, we've gotten data about all of the pets in the library. We've gotten a list of our pets. We've gotten total pets. Total pets tells us that there are 25 pets that are part of our library, but I might want to filter this list to see just the pets that are available or just the pets that are checked out.

00:18 To do this, I'm going to add a GraphQL argument. There's an argument on the totalPets query called status. This will take in either available or checked out. If we add Available, we'll see that there are 20 available pets.

If we change this to CHECKEDOUT, we'll see that the total checked out pets is five.

00:38 If we look at the totalPets query in the schema, we'll see that it has this optional status argument.


The value that I need to send is for PetStatus. PetStatus is an enum, either available or checked out. Now as we saw before, totalPets will work without a filter, but if I do provide a status filter, this will filter the list based on the value that I provide for PetStatus.

