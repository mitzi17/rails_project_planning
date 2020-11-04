# rails_project_planning- Event App

## What is the Many to many relationship and how is it used?
	User has_many :events
	  users/user_id/events
	User has_many :reviewed_events, through :reviews, source:events
	  users/user_id/events/event_id/reviews
	Event has_many :reviews
	  events/event_id/reviews
	Event has_many :reviewers, through :reviews, source:users
	  events/event_id/reviews/review_id/user

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
	  -date
	
	Review
	  -title
	  -content

## How do users fit into the application? How are they related to the other models?
	Users can login and create events and/or submit reviews

## What are our Nested Routes? (We need a nested new route and either a nested index or nested show route)
	users/:user_id/events -> shows all events created by a particular user
	users/:user_id/reviews -> shows all reviews by a particular user
	events/:event_id/reviews/new -> renders form to submit review of an event
	events/:event_id/reviews -> shows all reviews of a particular event
	
## Do we have Non Nested Versions of those nested routes?
	reviews/new -> form to submit a review
	events/new -> form to create an event
	
## What Scope Method(s) do we have and how are they used?
	 Event.type(:category) => music, cinema, exhibitions, festivals, corporate, sports, etc.
	 Event.order(price :asc, price :desc) => low to high, high to low

## What does the schema for our app look like?

```rb
# table migration for: users 
# t.string :name
# t.string :password_digest
class User

	# relationships
		has_many :events
		has_many :reviewed_events, through :reviews, source:events

	# validations 
		-name
		-password

	# user submittable attributes (if this is a join model)

	# scope_methods (if any)
	
# table migration for: events 
# t.string :name
# t.string :category
# t.string :location
# t.integer :price
# t.datetime :date

class Event 
	# relationships
		has_many :reviews
		has_many :users ??
		has_many :reviewers, through :reviews, source:users

	# validations 
		-name
		-location
		-category
		-date

	# user submittable attributes (if this is a join model)

	# scope_methods (if any)
		Event.type(:category) => music, cinema, exhibitions, festivals, corporate, sports, etc.
	 	Event.order(price :asc, price :desc) => low to high, high to low
		Event.upcoming (lambda { where("created_at >= ?", Time.zone.now ) })
	
# table migration for: reviews 
# t.string :name
# t.string :content

class Review 
	# relationships
		belongs_to :user
		belongs_to :event

	# validations 
		-title
		-content

	# user submittable attributes (if this is a join model)
		-title
		-content

	# scope_methods (if any)



end
```
