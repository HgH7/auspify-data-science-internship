# Part 3: Content-Based Recommendation System - Report

**Objective.** Build a recommender that, given any title, returns the 10 most similar titles in the catalog.

**Method.** TF-IDF over a combined text "soup" of genres, director, type, country, rating and release year; cosine similarity between all 8,787 titles; top-10 nearest titles returned per query.

**Key findings.**

- 84.3% of top-10 recommendations share the query title's primary genre, against 9.3% for random picks; 98.3% share at least one genre, against 23.8% random. The model beats chance by a wide margin.
- Demo: "Dick Johnson Is Dead" returns other recent documentaries (similarity 0.27-0.33); "The Crown" returns British drama series such as "The English Game", "Dracula" and "Black Mirror" (similarity up to 0.98).

**Limitations.** Content features only, with no viewing data, so it finds similar titles rather than personalized picks. Part 1 dropped the description and cast columns, so plot and actors are not used. The genre-based evaluation is partly circular, because genre is one of the features; it shows the model finds similar content, not that people would enjoy it. A natural improvement is to merge description and cast back into the features.
