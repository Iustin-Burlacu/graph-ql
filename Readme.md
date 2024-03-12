## GraphQL tutorial

* https://www.youtube.com/watch?v=5199E50O7SI&list=LL&index=3&t=685s

## Some problems with Rest API

* Over fetching: getting back more data than we need

* Under fetching: getting back less than we need, so we need to do multiple requests to different end points to collect all data

## GraphQL

* Single end point

* Apollo server: <https://www.apollographql.com/docs/apollo-server/getting-started/>

    ```bash
    npm install @apollo/server graphql
    ```

* Apollo explorer: graphic interface for testing queries => http://localhost:5555

* Start app

    ```bash
    npm start
    ```

* Query to get all games, and for each game get only id and title
    ```
    query Query {
        games {
            id,
            title
        }
    }
    ```

* Query to get a single game
    ```
    query GameQuery($id: ID!) {
        game(id: $id) {
            id,
            title
        }
    }
    ```

* Mutation to delete a game by id
    ```
    mutation DeleteMutation($id: ID!) {
        deleteGame(id: $id) {
            id,
            title,
            platform
        }
    }
    ```

* Mutation to add a new game
    ```
    mutation addMutation($game: AddGameInput!) {
        adGame(game: $game) {
            id,
            title,
            platform
        }
    }
    ```

* Mutation to update a game by id
    ```
    mutation editMutation($edits: EditGameInput!, $id: ID!) {
        updateGame(edits: $edits, id: $id) {
            id,
            title,
            platform
        }
    }
    ```
    ```
    Example of body request 
    {
        "edits": {
            "title": "test",
            "platform": ["test", "test2"]
        },
        "id": "1"
    }
    ```