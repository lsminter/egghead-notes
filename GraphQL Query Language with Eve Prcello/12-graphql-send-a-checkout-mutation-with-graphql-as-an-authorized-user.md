Instructor: 00:00 The next step I want to take is to actually check out a pet. The checkout mutation takes in an ID of a pet to check out. I need to look at the pets that are currently available and find a pet to check out.

00:10 I'll send the allPets query with a status Available filter. I'll grab the id, the name, and the category.

Let me scroll down a little bit to find out who I want to check out. I want to check out this STINGRAY called Switchblade.

00:23 In order to do so, I'm going to need to send S-2 as an ID. At this point, I can add one more mutation to our query document. Our mutation is going to be called checkout. We'll give the mutation an operation name of Checkout, and we'll use the checkOut mutation.

00:40 We'll pass the id of S-2, and we want to grab details about the pet, so we'll grab their name. Let's also get some details about the customer. The customer is going to be me, but I'll grab my name as well.

When I send the Checkout mutation, I should see the pet has been checked out, and I see the customer who has checked that pet out.

01:02 If we look at the checkout mutation, we see that this returns the checkout payload. The checkout payload gives us the entire customer object, the entire pet object, and the checkout date. These custom response objects that we can return for mutations are pretty cool. We're able to grab customer fields, pet details, and the checkout date, all bundled into one object.