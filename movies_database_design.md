I'm
# Design Document

## Movies Database

---

### Scope

**What is the purpose of your database?**

The purpose of this database is to store and manage information about movies, including titles, release years, directors, actors, user comments, and user-submitted ratings.

**Which people, places, things, etc. are you including in the scope of your database?**

- Movies  
- Actors  
- Directors  
- Users  
- Comments  
- Ratings  
- Movie-actor and movie-director relationships

**Which people, places, things, etc. are outside the scope of your database?**

- Movie genres  
- Box office or financial data  
- Streaming platforms  
- Production companies  

---

### Functional Requirements

**What should a user be able to do with your database?**

- View a list of movies  
- Search for a movie by title  
- See actors and directors associated with each movie  
- Add comments to movies  
- View others' comments  
- Rate movies on a scale (e.g., 1 to 5 stars)  
- View the average rating for each movie  

**What’s beyond the scope of what a user should be able to do with your database?**

- Edit or delete others' comments or ratings  
- View genre-specific or financial details  
- Personalized movie recommendations  
- Manage user accounts or login credentials  

---

### Entities and Relationship

**Entities and relationships:**

- `Movies (movie_id, title, release_year)`  
- `Actors (actor_id, name)`  
- `Directors (director_id, name)`  
- `Users (user_id, username)`  
- `Commentd (comment_id, user_id, movie_id, content, comment_date)`  
- `Ratings (rating_id, user_id, movie_id, rating_value)`  
- `Movie_Actor (movie_id, actor_id)`  
- `Movie_Director (movie_id, director_id)`  

**Relationships:**

- A movie has many actors (via `MovieActor`)  
- A movie has one or more directors (via `MovieDirector`)  
- A user can comment on many movies  
- A user can rate many movies  
- Each movie can have many comments  

![ER Diagram](https://i.postimg.cc/gkhtPw24/er-movie.jpg)

---

### Representation

**Which entities will you choose to represent in your database?**

- Movies  
- Actors  
- Directors  
- Users  
- Comments  
- Ratings  
- Movie_Actor  
- Movie_Director  

**What attributes will those entities have?**

- **Movies**: `movie_id (PK)`, `title`, `release_year`  
- **Actors**: `actor_id (PK)`, `name`  
- **Director**: `director_id (PK)`, `name`  
- **Users**: `user_id (PK)`, `username`  
- **Comments**: `comment_id (PK)`, `user_id (FK)`, `movie_id (FK)`, `content`, `comment_date`  
- **Ratings**: `rating_id (PK)`, `user_id (FK)`, `movie_id (FK)`, `rating_value`  
- **Movie_Actors**: `movie_id (FK)`, `actor_id (FK)`  
- **Movie_Director**: `movie_id (FK)`, `director_id (FK)`  

**Why did you choose the types you did?**

- IDs and rating as integers for indexing and rating  
- TEXT for comment, names, and title  

**Why did you choose the constraints you did?**

- Unique primary keys for entity identity  
- Foreign keys to maintain integrity  
- `NOT NULL` on critical fields (e.g., `movie title`, `rating_value`)  

---

### Optimizations

**Which optimizations (e.g., indexes, views) did you create? Why?**
  
- View to simplify movie browsing with average ratings and comment count  

---

### Limitations

**What are the limitations of your design?**

- Still no genre or categorization support  
- No login or password protection  
- No tracking of how many users watched a movie  
- Ratings are stored, but no logic to handle disputes or edits  

