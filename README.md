# MindSwarm - A real-time crowd-sourced knowledge app.

Build on the MERN stack with GraphQL.

## Models

```
User
  _id: ID!
  name: String! 
  username: String!
  email: String!
  password: String # Allow null because we don't want to return it
  questions: [Poll!]! # Ref to Poll
  answers: [PollOption!]! # Ref to PollOptions created by this User
  intellect: Float! # Average intellect across all answers based on upvotes
  createdAt: String!
  updatedAt: String!
  
Poll
  _id: ID!
  subject: String!
  author: User! # Ref to User
  options: [PollOption!]! # Ref to PollOptions appended to this Poll
  status: String! # Whether this poll has been closed or not
  createdAt: String!
  updatedAt: String!

PollOption
  _id: ID!
  submission: String!
  author: User! # Ref to User
  poll: Poll! # Ref to Poll where this option appears
  votes: [PollVote!]! # Ref to PollVotes cast on this PollOption
  createdAt: String!
  updatedAt: String!

PollVote
  _id: ID!
  value: Integer!
  author: User! # Ref to User
  option: PollOption! # Ref to PollOption where this PollVote was cast
  createdAt: String!
  updatedAt: String!
```

### NOTE:
The Users who provide PollOptions in a Poll are prevented from voting within that Poll.
Otherwise, people could sabotage the outcome of Polls and skew their intellect ranking.

## Technologies

### Back-End
- Node + Express
- MongoDB + Mongoose ORM
- Apollo Server v2
- WebSockets
- OpenID Connect (Google OAuth2)

### Front-End
- React 16+
- Apollo Client v2
- Styled Components

Heavily inspired by the work of @alex996 at Code Realm and @reedbarger on Udemy.