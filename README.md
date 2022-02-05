# Project Happy Thoughts API

I have been using Mongo to store data and set up express endpoints to fetch data. This week's project was to expose endpoints to my users to allow them to POST data to my API, and then use that data to save new objects in the Mongo database. 

## The problem
In the Happy Thoughts project,I built a frontend in React which uses an API we created to store thoughts. For this project, I have built my own API which works in the same way and should become a drop-in replacement for the API I used in the React frontend.

I used a ready-made frontend that has a form to write a new 'happy thought', lists recent thoughts, and shows a count of 'hearts' on each thought. Users could then click the heart to like a thought. 

In order to replace the API we built, I needed to build a Thought Mongoose model which has properties for the message string, a heart property for tracking the number of likes, and a createdAt property to store when the thought was added.
Then, I had to add 3 endpoints: 
`GET /thoughts`: This endpoint should return a maximum of 20 thoughts, sorted by `createdAt` to show the most recent thoughts first.
`POST /thoughts`: This endpoint expects a JSON body with the thought `message`, like this: `{ "message": "Express is great!" }`. If the input is valid (more on that below), the thought should be saved, and the response should include the saved thought object, including its `_id`.
`POST thoughts/:thoughtId/like`: This endpoint doesn't require a JSON body. Given a valid thought id in the URL, the API should find that thought, and update its `hearts` property to add one heart.

## View it live
frontend: https://haruahn-happiness-site.netlify.app 

backend: https://haruahn-happiness-api.herokuapp.com/
