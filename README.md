1. What would happen if an ArrayList was used instead of a HashSet? Is there an advantage to using a HashSet here?

2. We chose: ```java HashMap<String, HashSet<Movie>>``` for the tracker, which made it very easy to answer questions such as "What movies has Alice watched" or "What is Alice's total viewing time". Explain how a different design, such as ```javaHashMap<Movie, HashSet<String>>``` would make certain other questions very easy to answer and others more difficult.

[Markdown Guide](https://www.markdownguide.org/basic-syntax/)

1. If we used an ArrayList, we might gain some functionality in exchange for some efficiency.
Sets do not contain duplicate elements. Therefore, if we want to determine IF someone has a watched a movie,
it may be quicker than if we have to search a collection containing every single time someone watched a movie including rewatches.
On the other hand, suppose we are trying to determine trends in what users watch.
For example, maybe we want to figure out if people are likely to watch a movie's sequel after they finish the movie.
Having an unordered set makes it difficult or impossible to do this.
An ordered list on the other hand may allow us to do this, at the expense of allowing duplicate values.
Since our code is only trying to determine IF someone has watched a movie, using a HashSet gives us an advantage here, but may give us challenges elsewhere.
If we instead wanted to do something simple like count how many times someone has watched a movie, we would need to either alter our structure,
like allow the movie to track how many times it has been watched or replace the HashSet with an ArrayList and then count appearances of the movie object in the list.
Additionally, one advantage of hashing is that it allows some methods to run in O(1) time depending on size/implementation that we may not be able to get in
O(1) time for an ArrayList.

2. Using a structure with the format of ```HashMap<Movie, HashSet<String>>``` offers advantages if we are trying to pull information about which movies have been
watched by certain users. For example, say we wanted to determine if users of a certain movie share some quality.
Another question we might want answers to is "How long have people spent watching this movie?"
This structure gives us easy access to each of the movie's viewers (or at least a key we can use to find them elsewhere).
On the other hand, it makes it harder to perform analysis on which movies an individual has watched. Say we wanted to check if 
someone watches movies of a particular quality. This would be much more difficult with this alternate structure.
Ultimately, this structure gives us an advantage in answering questions centered around the movie,
while the other structure gives us an advantage in answering questions about the user.