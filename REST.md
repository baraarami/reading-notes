Introduction
Welcome to version 3 of The Movie Database (TMDB) API. Below you will find a current list of the available methods on our movie, tv, actor and image API. If you need help or support, please head over to our .

To register for an API key, click the  from within your account settings page. You can also view the screenshots below for help:

Click on your avatar or initials in the main navigation ()
Click the "Settings" link ()
Click the "API" link in the left sidebar ()
Click "Create" or "click here" on the API page ()
Please note that the API registration process is not optimized for mobile devices so you should access these pages on a desktop computer and browser.

Before being issued an API key you will have to agree to our terms of use. You can read that .

A few useful tips...

The  are useful to get the static lists of data we use throughout the database. You can find things like the languages, countries, timezones and translations that we use. The configuration method also holds useful image information.
Understanding the basics of our authentication is useful. 

Authentication
Application Authentication
Application level authentication on version 3 is controlled by one of either a single query parameter, api_key, or by using your v4 access token as a Bearer token. You can request an API key by logging in to your account on TMDB and clicking the "API" link in the left hand side bar of your account page.

API Key
Once you have been issued a key, an example request looks like this (replacing the <<api_key>> text with your own API key):

https://api.themoviedb.org/3/movie/76341?api_key=<<api_key>>
All throughout this documentation every method has a "Try it out" tab. This functionality will let your paste your API key (and other pertinent parameters) and make a live request to the API.

Bearer Token
Starting with version 4, we're now using a Bearer token for all user authentication but the ability to use this token with v3 is also supported. If you head into your account page, under the API section, you will see a new token listed called API Read Access Token. This token is expected to be sent along as a Authorization header. A simple cURL example looks like the following:

curl --request GET \
  --url 'https://api.themoviedb.org/3/movie/76341' \
  --header 'Authorization: Bearer <<access_token>>' \
  --header 'Content-Type: application/json;charset=utf-8'
Using the Bearer token has the added benefit of being a single authentication process that you can use across both the v3 and v4 methods. Which one you choose is however, completely up to you.

User Authentication
You can authenticate TMDB users within your application to extend the TMDB experience within your application. This will let your users do things like rate movies, maintain their favourite and watch lists as well as do things like create and edit custom lists—all while staying in sync with their account on TMDB.

User authentication is controlled with a session_id query parameter. You can generate a session_id by following these steps:

Create a new 
Get the user to authorize the request token
Create a new  with the athorized request token
For a complete walkthrough of what this looks like, take a read through .

Guest Sessions
Guest sessions are a second type of user authentication. They have limited permissions as they can only rate a movie, TV show and TV episode. Creating a guest session is as simple as calling the new guest session method.

Just like a fully authorized user session, guest sessions should be kept private as they tie a session within your application to a single token.


Daily File Exports
We have started publishing some daily ID file exports. These are not, nor intended to be full data exports. Instead, they contain a list of the valid IDs you can find on TMDB and some higher level attributes that are helpful for filtering items like the adult, video and popularity values.

Data Structure
These files themselves are not a valid JSON object. Instead, each line is. Most systems, tools and languages have easy ways of scanning lines in files (skipping and buffering) without having to load the entire file into memory. The assumption here is that you can read every line easily, and you can expect each line to contain a valid JSON object.

Availability
All of the exported files are available for download from http://files.tmdb.org. The export job runs every day starting at around 7:00 AM UTC, and all files are available by 8:00 AM UTC.

There is currently no authentication on these files since they are mostly useless unless you're a user of our service. This could change at some point in the future so if you start having problems accessing these files, check this document for updates.

Path	Name
Movies	/p/exports	movie_ids_MM_DD_YYYY.json.gz
TV Series	/p/exports	tv_series_ids_MM_DD_YYYY.json.gz
People	/p/exports	person_ids_MM_DD_YYYY.json.gz
Collections	/p/exports	collection_ids_MM_DD_YYYY.json.gz
TV Networks	/p/exports	tv_network_ids_MM_DD_YYYY.json.gz
Keywords	/p/exports	keyword_ids_MM_DD_YYYY.json.gz
Production Companies	/p/exports	production_company_ids_MM_DD_YYYY.json.gz
Example
If you were looking for a list of valid movie ids, the full download URL for the file published on April 28 would be:

http://files.tmdb.org/p/exports/movie_ids_04_28_2017.json.gz

Languages
Language support on TMDB is based on the language query parameter you send along with your request. You can specify one or two values (separated by a dash) with this parameter. Here's a breakdown of how this works.

The first is a bare  code. A simple example to request the German information of a lists items looks like:

https://api.themoviedb.org/3/movie/76341?api_key=<<api_key>>&language=de
Taking this a step further, knowing that some languages like Portuguese are available in different regions around the world, and you were only interested in Brazil, you can specify an extra  tag. A request for this more specific data looks like:

https://api.themoviedb.org/3/movie/76341?api_key=<<api_key>>&language=pt-BR
Only a limited set of combinations are supported as a translation source and we try to be smart about how this works. In my first example, calling only de is really the same as calling de-DE. By default, a bare ISO-639-1 language will default to its matching pair, ie. pt-PT. This is why in my second example above, I showed you how you can override that value with pt-BR. The last example to show you would be a request for pt-US. This is not a valid translation and will default to pt-PT.

We also provide a list of officially supported translations that generally have the best coverage of data

Images
You'll notice that movie, TV and person objects contain references to different file paths. In order to generate a fully working image URL, you'll need 3 pieces of data. Those pieces are a base_url, a file_size and a file_path.

The first two pieces can be retrieved by calling the  API and the third is the file path you're wishing to grab on a particular media object. Here's what a full image URL looks like if the poster_path of /kqjL17yufvn9OVLyXYpvtyrFfak.jpg was returned for a movie, and you were looking for the w500 size:

https://image.tmdb.org/t/p/w500/kqjL17yufvn9OVLyXYpvtyrFfak.jpg
Company and network logos are available in two formats, SVG and PNG. All of the logo_path fields will return a .png. This is to maintain backwards compatibility since SVG support was only added very recently. When looking at the image methods there is a new field called file_type that will show you the original version of the asset that was uploaded. For SVG's, you should call the original image size since we don't resize them. If you prefer to grab PNG's, you can call any size you wish just like normal.



Image Languages
poster_path: The poster_path will query the language you specify first and default back to the highest rated image of the items "original language" if it's present. If that image doesn't exist, it simply falls back to the highest rated. It's important to note that even though our language query parameter supports regional lookups, these regional variants are not supported for images at this time. This will be getting added at a later date.

backdrop_path: Since 99% of backdrops don't contain a language, the default lookup for a backdrop is to simply query for the highest rated backdrop that belongs to the given entry.

still_path: Like backdrops, TV episode images don't inherently have languages. We query for the highest rated.

In the event you query one of the distinct /images methods, there is a new way you can query additional languages by using the include_image_language query parameter. Think of this as kind of like a fallback. This is especially useful to grab two things. First, finding the backdrops and posters in a users specified language but also to grab all of the images that haven't been tagged with a language yet. Here's an example:

https://api.themoviedb.org/3/movie/550/images?api_key={api_key}&language=en-US&include_image_language=en,null
Notice the include_image_language parameter. This query (en,null) is looking for all images that match English and those that haven't been set yet (null).\


Regions
Region support is finally here! There's two aspects to this that I should go over. The first is the new region parameter.

The region paramater will act as a filter to search for and display matching release date information. This parameter is expected to be an  code.

For example, if you were searching for the movie Whiplash and wanted to show the German release date (to go with the German translation data of course) you can make a query like so:

https://api.themoviedb.org/3/search/movie?api_key=<<api_key>>&query=whiplash&language=de-DE&region=DE
In this case, region is simply acting as a presentation filter. In the event that we don't have a release date entered for the country you are searching for, we simply default back to the primary release date like always. This is the same as entering no region parameter.

Where this can get pretty amazing is with the  method because there's also a new with_release_type filter that can work in tandum with the region. Lets say you were looking for movies that are in the theatres in Germany this week. That's easy, we can now build this query:

https://api.themoviedb.org/3/discover/movie?api_key=<<api_key>>&language=de-DE&region=DE&release_date.gte=2016-11-16&release_date.lte=2016-12-02&with_release_type=2|3
You can of course sepecify any release type as found in our  documentation. If you do not specify with_release_type while using the region param on discover, it simply acts as a filter looking for any movies that match your filter criteria that has at a bare minimum, one matching release date for the country specified.

Popularity
Popularity is a very important metric here on TMDB. It helps us boost search results, adds an incredibly useful sort value for , and is also just kind of fun to see items chart up and down.

Each model builds their popularity value slightly differently. If you're curious as to the how and why, check out the information below.

Movies
Number of votes for the day
Number of views for the day
Number of users who marked it as a "favourite" for the day
Number of users who added it to their "watchlist" for the day
Release date
Number of total votes
Previous days score
TV Shows
Number of votes for the day
Number of views for the day
Number of users who marked it as a "favourite" for the day
Number of users who added it to their "watchlist" for the day
Next/last episode to air date
Number of total votes
Previous days score
People
Number of views for the day
Previous days score
There is no API to explore this data right now but it is something that would be a lot fun to dig into. The  do however, contain the popularity data so there is a record of the values starting on April 28, 2017.



JSON & JSONP
The only format we support is JSON. If you are using a JavaScript library and need to make requests from another public domain, you can use the callback paramater which will encapsulate the JSON response in a JavaScript function for you.

https://api.themoviedb.org/3/movie/550?api_key={api_key}&callback=test

Append To Response
The , , ,  and  detail methods support a query parameter called append_to_response. This makes it possible to make sub requests within the same namespace in a single HTTP request. Each request will get appended to the response as a new JSON object.

Here's a quick example, let's assume you want the movie details and videos for a movie. Usually you would think you have to issue two requests:

https://api.themoviedb.org/3/movie/157336?api_key={api_key}
https://api.themoviedb.org/3/movie/157336/videos?api_key={api_key}
With append_to_response you can issue a single request:

https://api.themoviedb.org/3/movie/157336?api_key={api_key}&append_to_response=videos
Even more powerful, you can issue multiple requests, just comma separate the values:

https://api.themoviedb.org/3/movie/157336?api_key={api_key}&append_to_response=videos,images
The best part of this is that these requests only count as one request against the rate limits so you can really speed up your experience.

Each method will still respond to whatever query parameters are supported by each indivudal request. This is worth pointing out for images since your language parameter will filter images. This is where the include_image_language parameter can be useful as outlined in the 

Search & Query For Details
A common workflow here on TMDB is to search for a movie (or TV show, or person) and then query for the details. Here's a quick overview of what that flow looks like.

1. Search
First, you are going to issue a query to one of the movie, TV show or person search methods. We'll use Jack Reacher and the movie method for this example:

https://api.themoviedb.org/3/search/movie?api_key={api_key}&query=Jack+Reacher
This will return a few fields, the one you want to look at is the results field. This is an array and will contain our standard movie list objects. Here's an example of the first item:

{
  "poster_path": "/IfB9hy4JH1eH6HEfIgIGORXi5h.jpg",
  "adult": false,
  "overview": "Jack Reacher must uncover the truth behind a major government conspiracy in order to clear his name. On the run as a fugitive from the law, Reacher uncovers a potential secret from his past that could change his life forever.",
  "release_date": "2016-10-19",
  "genre_ids": [
    53,
    28,
    80,
    18,
    9648
  ],
  "id": 343611,
  "original_title": "Jack Reacher: Never Go Back",
  "original_language": "en",
  "title": "Jack Reacher: Never Go Back",
  "backdrop_path": "/4ynQYtSEuU5hyipcGkfD6ncwtwz.jpg",
  "popularity": 26.818468,
  "vote_count": 201,
  "video": false,
  "vote_average": 4.19
}
2. Query For Details
With the item above in hand, you can see the id of the movie is 343611. You can use that id to query the movie details method:

https://api.themoviedb.org/3/movie/343611?api_key={api_key}
This will return all of the main movie details as outlined in the . I would also suggest taking a read through the  document as it outlines how you can make multiple sub requests in one. For example, with videos:

https://api.themoviedb.org/3/movie/343611?api_key={api_key}&append_to_response=videos



