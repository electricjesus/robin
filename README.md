#Robin

Open-source implementation of reddit's [robin](https://reddit.com/robin) chat system.

This is a living document! Feel free to contribute, make changes, and commit!

##Spec
- Users can pick their chat name. That username (and that user's unique identity) stays with them for their session.
- When a user joins for the first time, they enter a chatroom with one other user.
- Each chatroom can vote to: ABANDON, STAY, or GROW. Votes are by majority.
	- If they ABANDON, the chat room dissolves and each user goes back to the beginning.
	- If they STAY, a private subreddit is created for these users.
	- If they GROW, they will be merged with another chat room (of the same size? Or any other room?)
- Each user must choose each time a new vote is called. Failure to vote counts as an abandon vote.
	- Some people have complained that this makes growing difficult when people go to sleep, but I think that is a fair and organic result from the way Robin fosters communities of appropriate size.

##Stack
- Backend: Node.js + Express
- Messaging: Socket.io (WebSocket library)
- Data storage: None (chat rooms can remain in memory)
- Authentication: Reddit

##Ideas
(Not in the spec but would be interesting to try in the future)
- When a room votes to STAY, create a permanent chat room on joinrob.in (separate from reddit) to give the new community a place of their own
- Moderator status could be given to people with seniority (that have been in the room for more joins)

##Resources
- API endpoint for creating a subreddit: https://www.reddit.com/dev/api#POST_api_site_admin
- Socket.io documentation: http://socket.io/
- Reddit Oauth: https://github.com/reddit/reddit/wiki/OAuth2
