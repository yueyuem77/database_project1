# Proposal for a Game-Based Social Interaction Platform

## Short version
The application is a game-based social interaction platform where users can follow each other, post game reviews, create wish lists, and engage in discussions through replies to posts. Users will be able to add games to their personal wish lists, follow other gamers, and write reviews about specific games. Entities in the application include Users, Games, Posts, Replies, Follower lists, and Wish lists. Relationships such as "Users follow other users" and "Users write posts" will link these entities. Key attributes include usernames, game titles, post content, and timestamps for interactions. Real-world constraints include unique usernames, non-redundant game entries, and a limit on the length of posts. Data for the games will come from a combination of public game databases and user-generated entries. Users can browse games, add them to their wish lists, write reviews, and reply to other users' posts, creating an interactive experience similar to social media platforms. The challenge lies in handling dynamic interactions such as managing real-time replies and keeping the follower network updated efficiently.

## 1. Introduction

The goal of this project is to develop a web-based application that integrates gaming and social interaction features. The platform will allow users to interact with each other by following profiles, posting content, adding games to wish lists, and replying to posts. The application aims to foster a community-driven gaming ecosystem where users can share experiences, review games, and connect with others who have similar gaming interests.

## 2. Project Objectives

- Create a user-friendly platform that allows users to follow each other and maintain a list of followers.
- Allow users to write posts about games, which can include reviews, opinions, or questions.
- Enable users to add games to a personalized wish list.
- Foster discussions within the community through a reply feature to comment on posts.
- Provide features to track user activity and game preferences through followers and wish lists.

## 3. ER Diagram

![image](https://github.com/user-attachments/assets/a9e9e89a-6d69-4a72-8f4c-93ad429f00b6)

The following are the key features to be developed, based on the entity-relationship diagram:

- **Users**: Core entity representing registered users on the platform.
  - Has a unique identifier, user_id (Primary Key).
  - Can follow other users to build a network of followers.
  - Can create posts about games which might contains reviews for games
  - Can record the duration of game played
  - Can add game to wishlist

- **WishList**: Users can maintain a wish list of games they are interested in. This feature enhances user engagement by allowing them to bookmark games they wish to explore or purchase in the future. Wishlist is a Weak Entity
  - Primary key set consists of uid and gameid
  - If the user is deleted, the wishlist will be deleted.
  - If the game is deleted, the game will be deleted from the wishlist

- **Game**: Central to the platform, games are the items around which most interactions occur. Users can add games to their wish lists and write posts related to specific games.
  - Has a unique identifier (game_id, platform)
  - Game can be on multiple platform
  - has a detailed description of the game
  - has a rating for the game
  - has a release date


- **Posts**: Users can post content and share their thoughts on games.
  - Primary key is postid
    
- **Price**: Price is a weak entity set dependent on the existance of game. It is unique for every combination of game and country.
  - price of games varies across platform, country

- **Discount**: Discount is a weak entity set dependent on the existance of game and price
  - Discount is monitored by the platform
  - Can only last a pariod of time
  - time will not overlap in one country
  - different country will have discount on games
  - different platform will have different discount on games
## 4. SQL Schema
```
Create Table User(
	uid INT PRIMARY KEY, 
username VARCHAR(255) NOT NULL,
phone INT );


Create Table Post(
	postid INT PRIMARY KEY,
	uid INT,
	content TEXT,
	date DATE
);

Create Table Follow (
	follower_id INT REFERENCES  User, 
followee_id INT REFERENCES User,
PRIMARY KEY (follower_id, followee_id), 
);

Create Table Write_Post (
	uid INT references user,
	Postid INT references post,
	Primary key postid
);



Create table PLAY (
	Uid int references user,
	Gameid int references game,
	Platform str references game,
	Duration int,
	PRIMARY KEY (uid, gameid, platform)
);

Create table Add_game (
	Uid int references user,
	Gameid int references game,
	Platform str references game,
	PRIMARY KEY (uid, gameid, platform)
);

Create table Wishlist_Contain (
	Uid int references user,
	Gameid int references game
	Primary key (uid, gameid)
);

Create table Mention (
	Postid references post,
	Gameid references game,
	Platform references game,
	Primary key (postid)
);

Create table Worth (
	Gameid int,
	Platform str,
	Country str
);


	
CREATE TABLE Own_Wishlist (
	Uid INT references user,
	Gameid references 


Create Table Game(
	gameid INT NOT NULL,
	platform TEXT  NOT NULL,
description TEXT,
rating INT,
Release_date DATE, 
	PRIMARY KEY(gameid, platform)
);

Create Table Wishlist(
	gameid INT, 
	uid INT NOT NULL, 
	FOREIGN KEY uid REFERENCES Users(uid)
);
```



## 5. Technology Stack

- **Front-end**: Python
- **Back-end**: 
- **Database**: PostgreSQL or MySQL to handle relational data, managing users, games, posts, and relationships.
- **Authentication**: 
- **Hosting**: 


