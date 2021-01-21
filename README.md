# Analytics Engineer Challenge

Assignment:

Download this data https://www.kaggle.com/rounakbanik/the-movies-dataset and place it at the top level of this directory, in a subdirectory named moviearchive. 

We will be using the following files 
- movies_metadata.csv
- credits.csv
- ratings_small.csv
- keywords.csv

Your task is to generate tables with interesting feature based off of this input data. 
You will be spinning up a local MySql instance with Docker, and configuring another container to load the data into this database.

The outputs of the challenge are derived tables in the database:

Movie with percentile information for ratings
- Column 1: movie_id
- Column 2: movie title
- Column 3: Min rating
- Column 4: 25th percentile of ratings
- Column 5: 50th percentile of ratings
- Column 6: 75th percentile of ratings
- Column 7: Max rating

Keyword aggregates:
- Column 1: keyword id
- Column 2: keyword
- Column 3: # of movies which reference keyword

Cast-member aggregates
- Column 1: Cast member ID
- Column 2: Cast member name
- Column 3: # of movie featuring castmember

Only include counts and rows for movies that are included in the ratings_small.csv (it’s a subset of 9000ish movies).
Additionally please include one or two other derived tables calculating metrics of your choice. We would like to see what interesting features you see in the data.

Submit your code, as well as a markdown file including small write-up of the additional derived tables you’ve created, and what value can be derived from them.

We have provided a docker-compose file that defines the database container, and templates the appropriate environment variables for the db connection.
In order to complete the challenge you will need to add source code in the src/ directory to handle the database logic, and a Dockerfile that packages that source code.
The job service in the docker-compose file will build your dockerfile and run it next to the database. 

The acceptance criteria:
1. The src/ directory has been populated with any necessary source files. These can be a combination of SQL and/or your programming language of choice.
2. A Dockerfile has been added to the repo that packages the source code into a docker container
3. The following command should then build and launch your container alongside the database, and result in the DB open at localhost:3306 with all the appropriate data.
```docker-compose -p analytics-engineer-challenge up --force-recreate  --build```


You will be evaluated by the following:
1. Whether it works and the tables are generated as expected
2. Readability of your code/sql
3. How your design would scale to larger datasets
4. Quality of additional derived tables


Be prepared to answer questions like these in an interview:
1. How might you refactor for scale?
2. How would you deploy this job in a production environment?
3. What steps did you/could you have taken to validate the data outputs?

