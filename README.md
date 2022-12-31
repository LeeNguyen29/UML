Project 1: La La Land
You may work on and submit this project with one other person.

Overview
In this project, you will develop a UML model for chain of movie theaters and the films they are having showings for. Your final deliverables will consist of written text descriptions, UML diagrams, and an XML Schema document (.xsd) for a portion of the UML design.

Enterprise Description
A chain of movie theaters allows customers to browse showings of films and purchase tickets to see a showing. There are any number of individual theaters in the chain, and each one decides which films it will show, at what times, and in which of its rooms. Customers will be able to purchase tickets to individual showings, choosing a seat at the scheduled room when they do.

There is only one theater chain in this enterprise; you do not need to abstract a "Chain" type.

Films
Although real life theaters sometimes show non-"feature films" like UFC fights, special episodes of Twitch or YouTube streams, or international sporting events, Theaters in our system only show Films. Films have a title, a duration (in whole minutes), a release date (use "date" as the type for this field), and a rating (which can only be "NR", "G", "PG", "PG-13", "R", or "NC-17"). Each Film is labeled with one or more genres like "action", "drama", "comedy", etc.; with no definite limit on the number or names of potential genres.

Theaters and their Rooms
A Theater is a physical business comprised of many Rooms (screens) where a film viewing can be scheduled. A Theater has a street address, city, state, and ZIP code.

Each Room of a Theater is given a name/title, e.g., "Screen 1", "IMAX 4", etc. A Room also has a capacity (total number of seats). Finally, a Room can show any number of film Formats, like "Standard", "3D", "IMAX", "ScreenX", or newer technologies as they are released.  Not every Room in a Theater will support the same Formats.

Rooms have many Seats, each of which has a name like "14A", "Seat 12", "Accessible Seat 5", etc. Some seats are identified with special labels to indicate features that distinguish them from typical seats. This could be "accessible seating", for guests who need easy physical access to their seat; "obstructed view", for seats that are behind railings or poles that make it hard to see; "reclining", for seats that can lean forward and back; and presumably any other label added by a theater. (In other words, this is not an exhaustive list of seat labels.)

Showings and Tickets
A Theater chooses when to show a particular Film, in which of its Rooms, and calls that a Showing. 

Tickets can be purchased for a Showing. Each Ticket has a face value (the price paid by the customer) and a distinct number, and also selects a Seat from the Room of the Showing.

Your Assignment
For each of the bolded Classes in the Enterprise Description (Film, Theater, Room, Seat, Showing, Ticket) you must complete and turn in:

A description of the class. I will hold you to a higher standard than in Homework 2. A good description will:
Focus on the Big Picture of the class and its relationship to other classes, without getting into philosophical definitions. 
Briefly indicate the cardinality of its relationships to other classes. ("A Theater [...] has many Rooms [...]")
Limit itself to information relevant to the Enterprise requirements. (There is only one chain, and they only show films. We don't need to know who owns a theater, what actors are in a film, who the director is, etc.)
Not list attributes that will be obvious in a UML diagram. It is OK to reference other classes.
Not be very long. It's not an essay, and it's not a documentation of every possible use case of the class.
Here is an example description for the Ticket class. The 323 plagiarism policy dares you to turn this in as your own work:

"A Ticket reserves a Seat for one particular Showing of a Film at a Theater."

A UML diagram of the class. You will complete and turn in a single UML diagram for the whole system. You must diagram:
Each of the classes from the model. Classes should be named in singular tense, e.g., "Film" not "Films".
Any natural attribute relevant to the enterprise description, along with a type for the attribute. Stick to the standard primitive types: int, float, bool, string; and to the types for representing dates and times: date (a year/month/day), time (hour/minute/second), and timestamp (a date and time together).
The associations/relationships between the classes. Each relationship must include:
A verb descriptor of the association, with an arrow indicating the direction of action or ownership. For example, an association between Room and Seat might read "arranges ➡" with the arrow pointing toward Seat, since a Room arranges many Seats.
The cardinalities of the association at each end. You must correctly distinguish between cardinalities like 0..1, 0..*, 1..*, and 1..1. 
Do not model fields to represent the associations, e.g., do not add a field of type Seat to the Ticket class to represent "the Seat reserved by the Ticket"; this field is already implied by the association.
You must also diagram any enumeration-type classes for solving the Enumerated Domain or Repeated Attribute problems from lecture. You do not need to write descriptions for these classes, but you must create a UML class diagram for them and show the associations they are involved in.
Third, you implement a portion of your model as an XML Schema document (XSD).

Specifically, your Schema will implement your UML model for the Theater, Room, and Seat classes.
You will define <theater>, <room>, and <seat> element types in your XSD, including all the attributes of those types from your UML model, and nesting the elements to reflect the one-to-many associations between the three UML classes.
It is not a requirement, but you should consider creating a .xml document to represent a single theater, its rooms, and the seats of the rooms, then see if your XSD validates it. This can be a helpful exercise for uncovering errors in your schema.
Design Considerations
Your design must accommodate these considerations:

Illegal tickets
Your design must make it impossible to create a Ticket that does not reference a legal Showing. For example, if a Ticket has its own "show time" timestamp field, then we could create a fake Ticket that references a Film and then sets a show time that does not correspond to an actual Showing. 

Arbitrary film ratings
It should be impossible for a Film to have a rating other than the ones listed above.

Redundancy and integrity
Your design must minimized redundant data. Eliminate association redundancy by carefully considering when an association between two classes is not needed because of an existing association. Eliminate attribute redundancy by isolating attributes to the class they describe, and don't copy them to other classes unless you can justify that the attribute represents something distinct. Eliminate value redundancy by using classes to represent new types, instead of strings, especially when the string is a label for a real thing (like a film format) or abstract concept (like a film rating).

You must correctly apply the Enumerated Domain and Repeated Attribute patterns to address redundancy and integrity issues. 

Deliverables
You must deliver to me, via Dropbox, a single PDF containing the following documents:

Title page (name of course, title of assignment, team member names, due date)
Class descriptions
UML diagram for the entire system
XML Schema definition for Theater, Room, and Seat classes.
Piece of cake :).
