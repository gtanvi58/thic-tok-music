# THIC-TOK MUSIC DISCOVERY<br/> Discover.. Play... Connect....
An enhanced music discovery system for new artists on TikTok. <br/>

## Setup
### Initial Setup

### Database: <br/>
Register at [MongoDB](https://www.mongodb.com/cloud/atlas/register) and create a cluster in mongoDB Atlas. This service is a free nosql database hosted on the cloud.<br/>


### API access
Youtube API: Access to youtube API in order to run the project. Follow instructions laid out at [Youtube API](https://developers.google.com/youtube/v3/getting-started)<br/>
Spotify API: Create a developer account at Spotify. Follow instructions laid out at [Spotify API](https://developer.spotify.com/documentation/web-api/tutorials/getting-started)<br/>

In order to run our app, you will need to generate access token for spotify. Run the python notebook at https://github.com/gtanvi58/thic-tok-music/blob/master/Algorithms/tiktokalgosApi.ipynb in Google Colab. Make sure to paste the redirect url in the input field of the 2nd cell. Copy the access token for future use.<br/>

### Environment Files
Refer to the following sample environment files to see what environment variables need to be set.<br/>

1. Backend Server env file:<br/>
Create a .env file in the project root folder of the /backend folder. Populate the mongodb database url and database name here. Database name is the cluster name that you created in mongodb. Refer to https://github.com/gtanvi58/thic-tok-music/blob/master/backend/sample_env_file.txt<br/>

2. Frontend Server env file:<br/>
Create a .env file in the project root folder of /frontend-changes folder. Populate your spotify developer details including the access token you generated by running the python notebbok on Colab. Refer to https://github.com/gtanvi58/thic-tok-music/blob/master/frontend-changes/Sample_Env_File.txt and https://github.com/gtanvi58/thic-tok-music/blob/master/Algorithms/tiktokalgosApi.ipynb.<br/>

3. Recommendation Enginer server env file: <br/>
Create a .env file in the project root folder of /python-notes folder. Populate the details as required. Refer to https://github.com/gtanvi58/thic-tok-music/blob/master/python-notes/sample_env_file.txt.<br/>


### Installing the dependencies
Once the environment files have been created, we will need to install the required libraries. Make sure NodeJs and Python is installed in your system. ([NodeJS](https://nodejs.org/en/download/package-manager/current), [Python](https://www.python.org/downloads/))<br/>

1. Navigate to backend folder (cd backend from project root folder) and run npm install command.<br/>
2. Navigate to frontend-changes folder (cd frontend-changes from project root folder) and run npm install command.<br/>

Ensure that the following libraries are installed in your python environment. All of these can be installed in your python environment using the pip install library-name in the command line terminal.<br/>

1. FastAPI (Refer to [Fast API](https://fastapi.tiangolo.com/#installation))<br/>
2. spotipy (Refer to [Spotipy](https://spotipy.readthedocs.io/en/2.24.0/#installation))<br/>
3. pydantic (Refer to [Pydantic](https://docs.pydantic.dev/latest/))<br/>
4. pandas (Refer to [Pandas](https://pandas.pydata.org/))<br/>
5. numpy (Refer to [Numpy](https://numpy.org/))<br/>
6. googleapiclient.discovery (Refer to [GoogleDeveloperClient](https://github.com/googleapis/google-api-python-client))<br/>
7. pymongo (Refer to [PyMongo](https://pymongo.readthedocs.io/en/stable/))<br/>
8. cachetools (Refer to [cachetools](https://pypi.org/project/cachetools/))<br/>
9. dotenv (Refer to [Dotenv](https://pypi.org/project/python-dotenv/))<br/>
10. librosa (Refer to [Librosa](https://librosa.org/doc/latest/install.html))<br/>
11. pytube (Refer to [PyTube](https://pytube.io/en/latest/))<br/>
12. pydub (Refer to [PyDub](https://pypi.org/project/pydub/))<br/>

### Database Initialization

Once all the libraries have been installed, it is time to initialize the database collections. Make sure the environment files have been created and the required details has been set in it. To run the data initialization script, navigate to /backend (cd backend) and run node init.js This will create 4 Collections <br/>
1. artists<br/>
2. users<br/>
3. videos<br/>
4. games<br/>

It also inserts dummy data into it that we have used across our project. <br/>

## Running our application

We have 4 server processes running in our application that talk to each other through REST APIs. This is in adherence to microservices pattern that we wanted to implement. <br/>

Following is how to run them. Ensure to run them in the following order.<br/>
1. To run the Piano Tiles Game Fast API server, navigate to python-notes from project root (cd python-notes) and run python app.py <br/>
2. To start database access Express server, navigate to backend from project root (cd backend) and run node index.js command <br/>
3. To start recommendation engine Fast API server, navigate to python-notes from project root (cd python-notes) and run python algorithms.py<br/>
4. Finally, to start the front end React server, navigate to frontend-changes from project root (cd frontend-changes) and run npm start command <br/>

Voila! You have your own music discovery application running!!

## Discover!! Play!! Connect!!!

### Inspiration
We drew inspiration from the engaging and addictive nature of music in interactive games like Piano Tiles and Guitar Hero, where players are immersed in dynamic musical experiences that naturally introduce them to new songs and genres through various levels and challenges. Additionally, we were inspired by Spotify's Daily Mixes, which curate personalized playlists based on users' listening habits and preferences, leveraging data-driven algorithms to offer a highly customized music discovery experience. By combining these elements, we aim to make music discovery on TikTok  both interactive and personalized, enhancing user engagement and fostering a deeper connection to diverse musical content. <br/>
### Goals and Objectives
Our solution aligns with the goals of building a simple music discovery feature and enhancing the artist/fan community by utilizing the Music and Artist Discovery feature and the Daylist. These tools create an intuitive way for users to discover new and diverse music, supporting increased exposure, content diversity, and the viral spread of music. Additionally, the Artist Discovery feature highlights new artists and showcases those followed by friends, while the Music Tiles game engages users interactively. This fosters a sense of community by connecting users with new artists and their friends' musical interests. <br/>
To ensure data consistency across platforms, we utilize the Spotify Web API and Atlas MongoDB for accurate and consistent data collection and retrieval. This ensures seamless integration and reliable performance across TikTok, Spotify, and other music platforms. Leveraging Atlas MongoDB's cluster creation, replication, and sharding capabilities ensures high availability and scalability, supporting the platform's growth and the increasing demand for music discovery features. <br/>

### Our Solution

1. Database: <br/>
We utilized Atlas MongoDB as our database solution, taking advantage of its cluster creation, replication, and sharding capabilities to ensure high availability and scalability. The database structure is inspired by Spotify’s WebApi. <br/>

2. Tables and attributes: <br/>
Artist Table: <br/>
_id, SpotifyId, Username, popularity_score, genres, spotify_follower_count, tiktok_follower_count, total_views_count, total_likes_count, total_share_count, total_video_count <br/>
Games Table: <br/>
_id, Track_ID, Track_Name, Artist, Scores <br/>
User Table: <br/>
_id, username, bio, spotify_id, following_friends, following_artists, liked, preference <br/>
Videos Table: <br/>
_id, Track_ID, Track_Name, Acousticness, Danceability, Energy, Instrumentalness, Liveness, Loudness, Speechiness, Tempo, Valence, Duration_ms, Creator_Artist_IDs, Popularity, Creation_Time, Description, Like_Count, Share_Count, View_Count, CDN_URL, Genres, youtube_link <br/>
Each table and its attributes serve specific purposes, facilitating the storage and retrieval of data related to artists, games, users, and videos within your MongoDB database setup using Atlas MongoDB. <br/>

3. Some important terminologies: <br/>
Genre map:  A 2D array organizing similar genres into cohesive groups for streamlined categorization and analysis. <br/>
New artist popularity score:This custom metric nicknamed (STanRi’s measure of popularity) enhances the visibility of emerging artists based on their content quality relative to their follower count. It assigns higher scores to artists with fewer followers but exceptional content, moderate scores to established artists with average content, and lower scores to artists with subpar content. <br/>

Formula:  <br/>

Rationale for Weight Assignments: <br/>
Total Likes Count (Weight: 1.5): Likes are given less weight because not everyone who enjoys content actually clicks the like button. It's a measure of appreciation but not an absolute indicator of quality or enjoyment. <br/>
Total View Count (Weight: 2): Views are weighted higher because they directly reflect the popularity and reach of the content. Higher views generally suggest higher quality and more widespread appeal. <br/>
Total Shares (Weight: 1.8): Shares carry more weight than likes but less than views. Sharing indicates a higher level of appreciation as users are willing to endorse the content with their networks, although not all viewers share content they enjoy. <br/>
Total Followers Count (Spotify and TikTok) (Weight: 3): Followers on both platforms are heavily weighted because they signify the artist's existing fan base and potential reach. Artists with more followers are likely more established and hence we will need a higher value to bring down the total score <br/>
Popularity Score (Spotify) (Weight: 3): The Spotify popularity score is weighted similarly to total followers count. A high score indicates broader popularity among listeners, and hence we will need a higher value to bring down the total score <br/>

Bootstrap resampling:  Bootstrap resampling is a statistical method used to estimate the distribution of a statistic by iteratively sampling with replacement from the original dataset. This approach enables the empirical determination of uncertainty or variability in a statistic, without relying on assumptions about the data's underlying distribution. <br/>



We have developed two key components to enhance music discovery on TikTok, specifically for emerging artists: <br/>
1. Music and Artist Discovery through Upcoming Artist Recommendations and the Daylist Feature: <br/>
It showcases recommended new artists and a leaderboard for emerging talents, determined by New artist popularity score. Additionally, it highlights artists followed by friends but not yet followed by the user. <br/>
Daylist Feature: The Daylist feature aids users in discovering diverse content on the platform.  <br/>
Daylist Algorithm: <br/>
Objective: Curate a diverse list of 10 songs: 3 from the user's preferred genre, 4 from genres similar to their preferences, and 3 from unrelated genres. <br/>
Procedure: <br/>
Calculate an embedding where each element represents target acousticness, danceability, energy, and instrumentalness. <br/>
Factors contributing to target acousticness: Instrumentalness, Liveness, Speechiness <br/>
Factors contributing to target danceability: Tempo, Energy, Valence, Loudness<br/>
Factors contributing to target energy: Loudness, Tempo, Valence, Liveness, Speechiness<br/>
Factors contributing to target instrumentalness: Speechiness, Liveness<br/>
Compute a weighted sum of factors of these characteristics using bootstrap resampling.<br/>
Formula:<br/>
 
We use this method to assign weights because the influence of each factor on a user's characteristic features evolves over time. Therefore, it is impractical to predetermine the values.<br/>
Determine the Euclidean distance between these target features and the features of a track. The track with the smallest distance is considered most similar to the target characteristics.<br/>
Extract the genre of these tracks, use a genre map to identify similar and dissimilar genres, and curate the playlist using the Spotify recommendation API by passing the genres and target characteristics of the songs.<br/>
Algorithm for Recommending New Artists:<br/>
Objective: Recommend new and upcoming artists based on the user's genre preferences.<br/>
Procedure:<br/>
Calculate the closest genres using the same approach as for the Daylist feature.<br/>
Based on the user's genre preferences and the new artist popularity score, recommend the top 10 emerging artists.<br/>
2. Piano Tiles<br/>
The Piano Tiles feature offers users an engaging and interactive way to enjoy songs from their Daylist, new artists, and their favorite artists through a dynamic game format. As users play, the speed of the tiles increases progressively, enhancing the challenge and excitement. A leaderboard ranks players based on their high scores for each song, fostering a competitive and enjoyable experience.<br/>
Game Rules:<br/>
Starting the Game:<br/>
Users select a song from their Daylist, a new artist, or their favorite artist to begin playing.<br/>
The game starts at a moderate speed, which gradually increases as the game progresses.<br/>
Scoring:<br/>
Users must click on the moving tiles in sync with the music to score points.<br/>
Each successful tile click increases the user's score.<br/>
Tile Interaction:<br/>
Clicking directly on a tile earns points. The more accurately users click on the tiles, the higher their score will be.<br/>
If users click outside of a tile, they lose the game immediately.<br/>
Speed Progression:<br/>
The speed of the tiles increases incrementally based on the duration of play. The longer the user plays, the faster the tiles move, requiring quicker reflexes and sharper focus.<br/>
Leaderboard:<br/>
A leaderboard displays user rankings for each song based on their high scores.<br/>
Users can view their position relative to other players, motivating them to improve their scores and climb the ranks.<br/>
Game Over Conditions:<br/>
The game ends if a user misses a tile or clicks outside of a tile.<br/>
High Score and Progress Tracking:<br/>
The game tracks high scores for each song, allowing users to see their best performances.<br/>
Progress is saved so users can aim to beat their previous high scores in subsequent gameplay sessions.<br/>
Game Development Logic: <br/>
1. Loading Audio<br/>
First, we start by loading the audio file. This means converting the MP3 file into a format that the computer can understand and work with.<br/>
2. Onset Strength<br/>
We calculate the onset strength of the audio signal. Onset strength measures sudden changes or peaks in the audio, which often indicate the start of a musical note.<br/>
3. Onset Detection Parameters<br/>
There are several settings we adjust to find these onsets:<br/>
pre_max and post_max: These help determine how big of a change in sound we're looking for, before and after a point in time.<br/>
pre_avg and post_avg: These help smooth out the changes in sound, making sure we're not picking up too many small variations.<br/>
wait: This setting makes sure we don't pick up onsets that are too close together in time.<br/>
delta: This sets a threshold for how much of a change in sound we need to consider it an onset.<br/>
4. Initial Onsets<br/>
Using the onset strength, we identify the initial times where there might be a musical note starting. These are our first guesses at where the notes begin.<br/>
5. Peak Picking<br/>
To refine our initial guesses, we look for peaks in the onset strength. These peaks are the strongest indications that a musical note is starting, and we focus on these to pinpoint the exact times.<br/>
6. Filtering<br/>
We make sure that the detected onsets are spaced apart by at least a minimum interval of time. This helps filter out rapid changes or noise in the audio signal that aren't actual musical notes.<br/>
7. Output<br/>
Finally, we get a list of times where we believe significant musical notes begin in the audio. These times are where the music starts to change or a new note is played, based on our analysis of the audio signal.<br/>

### Architecture:
1. Database:<br/>
We have chosen to host our database on a private MongoDB Atlas cluster due to its high scalability and availability. This setup leverages sharding and replication to distribute data across multiple servers, ensuring seamless scalability and redundancy. MongoDB Atlas offers comprehensive monitoring capabilities via its web interface, providing real-time insights into metrics such as current database size, the number of data reads and writes within a specified timeframe, and the number of active connections. Security is a paramount consideration, and MongoDB Atlas allows us to enhance it by whitelisting specific IP addresses that can access the database, ensuring controlled access. Additionally, user isolation further strengthens our security posture by segregating user data access. The NoSQL nature of MongoDB, which supports JSON document storage, aligns perfectly with our data structure requirements. This allows us to store and query data in its native JSON format, streamlining data handling and manipulation. The tables we have created are designed to offer flexibility and ease of implementation, enabling efficient data manipulation and retrieval. Our database connection architecture employs the singleton pattern, ensuring that each API call within a session uses a single, consistent database connection. This approach prevents the exhaustion of the database connection pool, maintaining optimal performance and reliability. By utilizing MongoDB Atlas, we achieve a robust, secure, and efficient database solution tailored to our specific needs.<br/>

2. Middleware:<br/>
For each of our functionalities, we have implemented REST APIs, enabling us to leverage microservices architecture. Each component—artists, videos, and users—has its own dedicated API, promoting modularity and ease of maintenance. We have enforced a global rate limit of 1000 API hits per 15 minutes to ensure fair usage and prevent abuse. To secure our APIs, we have protected the headers and implemented selective CORS, allowing access only from specific IP addresses, ports, and content types. All sensitive credentials, such as the database URL, username, password, and API keys, are securely stored in environment files to enhance security. Additionally, we have implemented response caching to minimize redundant database queries, thereby improving performance and reducing load on the database.<br/>

3. FrontEnd:<br/>
To fully leverage microfrontend architecture, we have ensured that no global variables are used across our UI screens. Each UI screen is designed to be self-contained, with its own isolated state and logic. This approach enhances modularity, making it easier to develop, test, and maintain individual components independently. By keeping UI screens self-contained, we also improve the scalability and flexibility of our frontend, allowing different teams to work on separate parts of the application without causing conflicts or dependencies on shared state.<br/>

### Outcomes<br/>
Our solution enhances exposure for emerging artists through the Music and Artist Discovery feature, which recommends new artists based on user preferences and friend networks. This increases the visibility of independent musicians and helps artists with good content widen their audience through the new artists leaderboard. As a result, emerging artists gain more exposure, leading to greater recognition and potential career opportunities. Additionally, the Daylist feature curates a diverse list of songs from various genres, both related and unrelated to user preferences, ensuring that users are introduced to a broader range of music. This promotes a more diverse and personalized content consumption experience, allowing users to explore different genres and styles they might not typically encounter.<br/>
To boost viral potential and engagement, the Piano Tiles game offers a dynamic and engaging way to discover music. By playing the game and sharing their scores, users contribute to the viral spread of songs and artists. The interactive nature and competitive element of the game encourage users to share and promote new music, increasing the chances of songs going viral. Furthermore, the social aspects of the Artist Discovery feature, such as seeing what friends are following, foster active engagement and interaction with the content. This deepens users' connection to the music and artists, building a stronger community around shared musical interests and enhancing their overall connection to the platform.<br/><br/><br/><br/>

### Tools <br/> 
React.js, MongoDB, Express, NodeJS, Python, Spotify WebAPI, Youtube API, JavaScript <br/>






