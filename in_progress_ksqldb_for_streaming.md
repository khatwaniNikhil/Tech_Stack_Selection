# Reference
https://www.youtube.com/watch?v=D5QMqapzX8o

# Sample Streaming use case -  movie records
1. movie data in a relational database
2. ingest into kafka movies topic (as soon as movie records are inserted into database table)
  ## Option 1 Using Kafka directly
   1. using Kafka connect(has a huge library of connectors available)
   2. requires you start a separate cluster
 ## Option 2 Using Ksql db
    1. start up a connector with a sql statement without starting a separate cluster as 2.1.1
    2. register that topic with Ksql DB as a table

# todo
to do this now as an established part of
the Kafka ecosystem connect has a huge
library of connectors available for it
but normally requires you to stand up a
separate cluster to run them here in
case equal DB I can start up a connector
with this sequel statement without
having to stand up a connect cluster of
my own the connector is now running
constantly producing new movie records
into the movies topic just as soon as
they're inserted into the database table
so those movie records have come into a
Kafka topic and now we'll register that
topic with Kay sequel DB as a table the
connector has already prepared the data
in the format we need with the message
key being the movie ID and the value
being the movie record itself you can
see all the movies are there but what
are we doing with those movies well the
application we're building is a movie
rating system imagine we have a large
community using a mobile app to rate
movies that they're watching at home
since they tell me it's rude to use your
phone at the movies every time the user
selects a movie on the app and taps a
rating we get a message produced to our
ratings topic I'm using a script to
simulate those ratings here since that
mobile app doesn't exist yet but still
will enrich and average those ratings
and since averages are no good if you
can't read them we'll also want to be
able to query the results when the
streaming application is up and running
anyway those ratings by themselves are
not very informative it's just a bunch
of numbers so let's try joining them
with the table we just made now we're
getting somewhere
at least we see movie titles
but what we really want is to group them
by title and then average the ratings
this is a much more interesting
operation we're beginning to get a sense
for the average preferences of our movie
rating public and it looks like they're
pretty sensible and notice something
else it's put all the data we need in
one place and it keeps it constantly
updated if we're building a web app or a
mobile front end we wouldn't want to go
stitching all these things together
every time we need to build a page now
let's make this a little bit more
official by creating a materialized view
of the results
this view is constantly running inside
the case equal DB engine consuming new
ratings as soon as they appear on the
ratings topic and updating the averages
in the table in real time and it's fine
to dump that table out to the CLI like
we've been doing but I've got specific
questions about these movies we want to
see these averages right personally I
want to know what people think of Super
Mario Brothers I want to know how
diehard is doing I want to know if Tree
of Life is as polarizing as it always is
so with these simple select queries what
we call pull queries in case equal DB we
can read those values from the table
using plain old sequel and let me
contrast pull query with its counterpart
a push query our application might want
to pull particular results out of a
materialized view that's a pull query
like we just saw but it also might want
to subscribe to all the updates on a
view like this here I'm getting a stream
of all movie ratings as they happen
enriched with movie title metadata those
updates come to the app as messages
enter Kafka and are processed by K
sequel DB this is what we call a push
query and all this command line sequel
is great but you might have been
wondering how do we integrate this with
actual applications well k sequel DB has
a rest interface that lets us do all the
same things I've been showing you but
over HTTP here I'm querying that same
materialized view of average movie
ratings using a simple rest query and
curl so that's the basics of K sequel DB
you've got a streaming sequel engine to
define stream processing programs you've
got built in Kafka Connect and you've
got pool queries to enable you to read
the results of your stream processing in
real
case equals being developed in the open
on github and is completely free to use
so download it try this demo check it
out and let us know what you get started
building
