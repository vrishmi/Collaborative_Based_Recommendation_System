# IT492: Recommendation System: Group Project 2
# Group 6
#### Vrishmi Parikh (202318013)
#### Mahmood Topiwala (202318030)
#### Anurag Shukla (202318039)
#### Tanaz Pathan (202318056)

---
Data: MyAnime List

## Data Analysis


* anime: This file contains information about anime, including attributes like anime_id, title, synopsis, type, genre, etc. The key attributes are:

    - anime_id: The ID of the anime.
    - title: The name of the anime.
    - score_count: Number of users that scored the anime.
    - popularity_rank: Rank of anime based on its popularity.
    - watching_count: Number of users watching the anime.
    - completed_count: Number of users that have completed the anime.
    - on_hold_count: Number of users that have the anime on hold.
    - dropped_count: Number of users that have dropped the anime.
    - plan_to_watch_count: Number of users that plan to watch the anime.
    - score_10_count: Number of users that score the anime a 10. (And like this from scores ranging from 01-10)

* user: This file contains detailed information about users, including attributes like user_id, num_watching, num_completed, num_on_hold, num_dropped, num_plan_to_watch, mean_score. Key attributes are:

    - user_id: The ID of the user.
    - num_watching: Number of animes the user is currently watching.
    - num_completed: Number of animes the user has completed.
    - num_on_hold: Number of animes the user has on hold.
    - num_dropped: Number of animes the user has dropped.
    - num_plan_to_watch: Number of animes the user plans to watch.
    - mean_score: Mean score given by the user to animes.

* user_anime000000000000.csv to user_anime000000000069.csv: These files contain relationships between users and animes, with attributes like user_id, anime_id, favorite (binary), score, etc.

* anime_anime.csv: This file contains relationships between pairs of animes. Key attributes are:

    - animeA: The ID of the first anime.
    - animeB: The ID of the second anime.
    - recommendation: 0 or 1 depending on whether animeB is a recommendation of animeA.
    - related: 0 or 1 depending on whether animeB is related to animeA.

* user_user.csv: This file contains relationships between pairs of users, with attributes like userA (id of the first user), userB (id of the second user), and friends (0 or 1 depending on whether userA and userB are friends).

### Data Summary
There are 990,000 unique users and 13,000 unique animes in the dataset.

Each user has given an average of 130 ratings, while each anime has received an average of 10,000 ratings.

On average, users are watching approximately 11 anime, and the average number of completed anime by users is around 159.

The mean score for anime given by users is approximately 7.12 out of 10, with a normal distribution ranging between 4 and 10.

User activity metrics exhibit a right-skewed distribution, with a few users having exceptionally high values for metrics like num_watching, num_completed, and num_plan_to_watch.

There is a low positive correlation of mean score with attributes such as num_completed, num_watching, num_on_hold, and num_dropped, indicating no significant impact of these variables on mean score.

A trend is observed where anime titles with fewer episodes and lower member and watching counts tend to receive higher scores from users.

## Designing the collaborative-based system using user-user & item-item:

* As we had more number of users (100k) than number of items (13k), it made sense to choose item-item similarity method but for the sake of completion we've performed both.

##

## Comparison between the above two systems

* We can observe that matrix factorization methods outperformed the neighborhood method by more than 4.35%
* One more interesting observation is that even the worst item-item based neighborhood (1.464) method outperformed the best user-user based neighborhood method (1.466) method. This is because we have more number of users than number of items and we rather prefer small number of quality neighbor than large number of loosely related neighbors.
* Significance weighing plays a significant role: Weighing the similarity between two entities (based on number of corated) squeezed more accuracy out of neighborhood method and pushed the MSE below 1.40 
## Novelty
* Used a better significance weghing formula for discounting similarities between entities.

* ![image](https://github.com/DistilledCode/IT492_CollaborativeBased_RecSys/assets/107433905/f60a7986-ebdf-4328-acfa-871303750f7c)

where $\left|\mathcal{J}_{u v}\right|$ denotes the cardinality of co=rated item/user set. 
