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
CREATE TABLE User(
	uid INT PRIMARY KEY, 
username VARCHAR(255) NOT NULL,
phone INT );


CREATE TABLE Post(
	postid INT PRIMARY KEY,
	uid INT,
	content TEXT,
	date DATE
);


CREATE TABLE Game(
	gameid INT,
	platform TEXT,
description TEXT,
rating INT,
Release_date DATE, 
	PRIMARY KEY(gameid, platform)
);

CREATE TABLE Wishlist(
	gameid INT NOT NULL, 
	uid INT NOT NULL, 
	Add_date DATE,
	FOREIGN KEY uid REFERENCES User(uid)
);



CREATE TABLE Follow (
	follower_id INT REFERENCES User, 
followee_id INT REFERENCES User,
PRIMARY KEY (follower_id, followee_id), 
);

CREATE TABLE Write_Post (
	uid INT REFERENCES user,
	Postid INT REFERENCES post,
	PRIMARY KEY postid
);

CREATE TABLE PLAY (
	Uid INT REFERENCES user,
	Gameid INT REFERENCES game,
	Platform str REFERENCES game,
	Duration INT,
	PRIMARY KEY (uid, gameid, platform)
);

CREATE TABLE Add_game (
	Uid INT REFERENCES user,
	Gameid INT REFERENCES game,
	Platform str REFERENCES game,
	PRIMARY KEY (uid, gameid, platform)
);

CREATE TABLE Wishlist_Contain (
	Uid INT REFERENCES user,
	Gameid INT REFERENCES game
	PRIMARY KEY (uid, gameid)
);

CREATE TABLE Post_Mention (
	Postid INT REFERENCES post,
	Gameid INT REFERENCES game,
	Platform TEXT REFERENCES game,
	PRIMARY KEY (postid)
);

CREATE TABLE Worth (
	Gameid INT,
	Platform TEXT,
	Country TEXT
	PRIMARY KEY (gameid, platform, country),
	FOREIGN KEY (gameid, platform) REFERENCES Game(gameid, platform)
);

CREATE TABLE Price(
	gameid INT NOT NULL,
	country TEXT NOT NULL,
	Platform TEXT NOT NULL，
	Amount INT NOT NULL,
	PRIMARY KEY (gameid, country, platform)
	
	FOREIGN KEY (gameid, platform) REFERENCES Game(gameid, platform)  ON DELETE CASCADE
);

CREATE TABLE Discount(
	Gameid INT,
	Country TEXT,
	Discount_rate,
	Start_date DATE,
	end_date DATE,
	FOREIGN KEY  (gameid, platform) REFERENCES Game(gameid, platform)  ON DELETE CASCADE

);


CREATE TABLE Have_Discount (
	Gameid INT,
	Platform TEXT,
	Country TEXT,
	PRIMARY KEY (gameid, platform, country),.
	FOREIGN KEY (gameid, platform, country) REFERENCES Price(gameid, platform, country) ON DELETE CASCADE
);



```



## 5. Technology Stack

- **Front-end**: Python
- **Back-end**: 
- **Database**: PostgreSQL or MySQL to handle relational data, managing users, games, posts, and relationships.
- **Authentication**: 
- **Hosting**: 


