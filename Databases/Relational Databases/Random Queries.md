```sql
select movies.movie_title from movies where(select count(*) from movies_cast as A where A.movie_id <> movies.movie_id and A.actor_id in(select actor_id from movies_cast where movies_cast.movie_id=movies.movie_id)group by A.actor_id) > 0
```