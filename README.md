# rails_project_planning- Event App

## What is the Many to many relationship and how is it used?
	User has_many :events
	  users/user_id/events
	Event has_many :users
	  events/event_id/users

## What is the User Submittable attribute on the join model?
	Review model has the following user submittable attributes
	  :title
	  :content
	
## What Validations do we need?
	User
	  -name
	  -password
	
	Event
	  -name
	  -location
	  -category
	
	Review
	  -title
	  -content

## How do users fit into the application? How are they related to the other models?
	Users can login and create events and/or submit reviews

## What are our Nested Routes? (We need a nested new route and either a nested index or nested show route)

## Do we have Non Nested Versions of those nested routes?

## What Scope Method(s) do we have and how are they used?

## What does the schema for our app look like?

```rb
# table migration for: examples 
# t.string :name
# t.string :etc…
class Example 
	# relationships

	# validations 

	# user submittable attributes (if this is a join model)

	# scope_methods (if any)


end
```
