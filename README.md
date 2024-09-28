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

![image](https://github.com/user-attachments/assets/02cf318e-c4d5-4788-b443-1637b2681b3a)

The following are the key features to be developed, based on the entity-relationship diagram:

- **Users**: Core entity representing registered users on the platform.
  - Has a unique identifier, user_id (Primary Key).
  - Can follow other users to build a network of followers.
  - Can create posts about games.
  - Can post reviews for game


- **Wish List**: Users can maintain a wish list of games they are interested in. This feature enhances user engagement by allowing them to bookmark games they wish to explore or purchase in the future.
  - Primary key set consists of uid and gameid


- **Game**: Central to the platform, games are the items around which most interactions occur. Users can add games to their wish lists and write posts related to specific games.
  - Has a unique identifier (game_id, platform)
  - Game can be on multiple platform
  - The application will maintain a catalog of games that users can interact with.

- **Posts**: Users can post content and share their thoughts on games.
  - Primary key is postid
 
    
- **Price**: Price is a weak entity set dependent on the existance of game. It is unique for every combination of game and country.

- **Discount**
 - Discount is monitored by the platform
 - Can only last a pariod of time
 - time will not overlap in one country
 - different country will have discount on games
 - different platform will have different discount on games
## 4. Technical Design Overview

- **Database Design**: The database will manage several entities, including `Users`, `Game`, `Post`, `Reply`, `follower_list`, and `wish_list`. The relationships between these entities will follow the diagram's structure.
  
- **User Interface**: The UI will allow users to navigate through the platform easily. Users will have access to their profiles, wish lists, follower lists, and posts. Interactive features such as posting content, adding games to wish lists, and replying to posts will be straightforward and intuitive.

- **Backend**: N/A

- **Security**: N/A

## 5. Technology Stack

- **Front-end**: Python
- **Back-end**: 
- **Database**: PostgreSQL or MySQL to handle relational data, managing users, games, posts, and relationships.
- **Authentication**: 
- **Hosting**: 


