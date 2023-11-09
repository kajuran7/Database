# Database

**1.Create a Database called movies?**
```
test> use movies
switched to db movies
movies>
```

**2.Create a collection called moviedetails.**

```
 db.createCollection("moviedetails")
{ ok: 1 }

```

**3.Create above 5 movie documents into a moviedetails collection.**

```
movies> db.MovieDetails.insertMany([
 {"Movie-Title": "Jurassic Park", "Genre": "Adventure", "Director": "Steven Spielberg", "Release Year": "1993"},
{"Movie-Title": "Forrest Gump", "Genre": "Drama", "Director": "Robert Zemeckis", "Release Year": "1994"},
 {"Movie-Title": "Titanic", "Genre": "Romance", "Director": "James Cameron", "Release Year": "1997"},
{"Movie-Title": "The Dark Knight", "Genre": "Action", "Director": "Christopher Nolan", "Release Year": "2008"},
 {"Movie-Title": "Avatar", "Genre": "Science Fiction", "Director": "James Cameron", "Release Year": "2009"}
])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("654c8a3fa3760b71c6a0b0d5"),
    '1': ObjectId("654c8a3fa3760b71c6a0b0d6"),
    '2': ObjectId("654c8a3fa3760b71c6a0b0d7"),
    '3': ObjectId("654c8a3fa3760b71c6a0b0d8"),
    '4': ObjectId("654c8a3fa3760b71c6a0b0d9")
  }
}
```
**4.List all documents created.**

```
movies> db.MovieDetails.find()
[
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d5"),
    'Movie-Title': 'Jurassic Park',
    Genre: 'Adventure',
    Director: 'Steven Spielberg',
    'Release Year': '1993'
  },
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d6"),
    'Movie-Title': 'Forrest Gump',
    Genre: 'Drama',
    Director: 'Robert Zemeckis',
    'Release Year': '1994'
  },
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d7"),
    'Movie-Title': 'Titanic',
    Genre: 'Romance',
    Director: 'James Cameron',
    'Release Year': '1997'
  },
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d8"),
    'Movie-Title': 'The Dark Knight',
    Genre: 'Action',
    Director: 'Christopher Nolan',
    'Release Year': '2008'
  },
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d9"),
    'Movie-Title': 'Avatar',
    Genre: 'Science Fiction',
    Director: 'James Cameron',
    'Release Year': '2009'
  }
] 
```

**5.List James Cameron’s movies.**

```
movies> db.MovieDetails.findOne({ "Director": "James Cameron" })
{
  _id: ObjectId("654c8a3fa3760b71c6a0b0d7"),
  'Movie-Title': 'Titanic',
  Genre: 'Romance',
  Director: 'James Cameron',
  'Release Year': '1997'
}
```
**6.List  James Cameron’s movies released in 2009.**
```
movies> db.MovieDetails.find({ "Release Year": "2009" })
[
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d9"),
    'Movie-Title': 'Avatar',
    Genre: 'Science Fiction',
    Director: 'James Cameron',
    'Release Year': '2009'
  }
]
```

**7.Delete the movie which you don’t like.**
```
movies> db.MovieDetails.remove({"Movie-Title": "Forrest Gump", "Genre": "Drama", "Director": "Robert Zemeckis", "Release Year": "1994" })
DeprecationWarning: Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.
{ acknowledged: true, deletedCount: 1 }
```

**8.Add the movie which is your favourite.**
```
movies> db.MovieDetails.insertOne({"Movie-Title": "Leo", "Genre": "Action", "Director": "Lokesh Kanakaraj", "Release Year": "2023"})
{
  acknowledged: true,
  insertedId: ObjectId("654c94dda3760b71c6a0b0da")
}
movies> db.MovieDetails.find()
[
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d5"),
    'Movie-Title': 'Jurassic Park',
    Genre: 'Adventure',
    Director: 'Steven Spielberg',
    'Release Year': '1993'
  },
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d7"),
    'Movie-Title': 'Titanic',
    Genre: 'Romance',
    Director: 'James Cameron',
    'Release Year': '1997'
  },
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d8"),
    'Movie-Title': 'The Dark Knight',
    Genre: 'Action',
    Director: 'Christopher Nolan',
    'Release Year': '2008'
  },
  {
    _id: ObjectId("654c8a3fa3760b71c6a0b0d9"),
    'Movie-Title': 'Avatar',
    Genre: 'Science Fiction',
    Director: 'James Cameron',
    'Release Year': '2009'
  },
  {
    _id: ObjectId("654c94dda3760b71c6a0b0da"),
    'Movie-Title': 'Leo',
    Genre: 'Action',
    Director: 'Lokesh Kanakaraj',
    'Release Year': '2023'
  }
]
```
**9.List movie Directed  by Christopher Nolan in 1994.**
```
movies> db.MovieDetails.find({"Director": "Christopher Nolan","Release Year": "1994"})
```

**10.List out the Director’s Name in your document.**
```
movies> db.MovieDetails.distinct("Director")
[
  'Christopher Nolan',
  'James Cameron',
  'Lokesh Kanakaraj',
  'Steven Spielberg'
]
```


