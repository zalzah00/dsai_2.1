# Assignment

## Brief

Write the Python codes for the following questions.

## Instructions

Paste the answer as Python in the answer code section below each question.

### Question 1

Question: From the `movies` collection, return the documents with the `plot` that starts with `"war"` in acending order of released date, print only title, plot and released fields. Limit the result to 5.

Answer:

```python
for m in movies.find({"plot": {"$regex": "^War"}}).sort('released', pymongo.ASCENDING).limit(5):
    print(f"{m['title']} was released in {m['released']}. Plot: {m['plot']}")
```

### Question 2

Question: Group by `rated` and count the number of movies in each.

Answer:

```python
stage_group_rated = {
   "$group": {
         "_id": "$rated",
         # Count the number of movies in the group:
         "movie_count": { "$sum": 1 }, 
   }
}

pipeline = [
   stage_group_rated,
]
results = movies.aggregate(pipeline)

# Loop through the 'rated' documents:
for rate in results:
   print(rate)
```

### Question 3

Question: Count the number of movies with 3 comments or more.

Answer:

```python
pipeline = [
    # Stage 1: Group the comments by movie_id and count them
    {
        "$group": {
            "_id": "$movie_id",
            "comment_count": { "$sum": 1 }
        }
    },
    
    # Stage 2: Match the groups that have 3 or more comments
    {
        "$match": {
            "comment_count": { "$gte": 3 }
        }
    },
    
    # Stage 3: Count the number of resulting documents (i.e., movies)
    {
        "$count": "movie_count"
    }
]

results = comments.aggregate(pipeline)

# The result is a single document with the count
for result in results:
    print("Number of movies with 3 or more comments:", result["movie_count"])
```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
