# Proposal for a Game-Based Social Interaction Platform

## 1. Introduction

The goal of this project is to develop a web-based application that integrates gaming and social interaction features. The platform will allow users to interact with each other by following profiles, posting content, adding games to wish lists, and replying to posts. The application aims to foster a community-driven gaming ecosystem where users can share experiences, review games, and connect with others who have similar gaming interests.

## 2. Project Objectives

- Create a user-friendly platform that allows users to follow each other and maintain a list of followers.
- Allow users to write posts about games, which can include reviews, opinions, or questions.
- Enable users to add games to a personalized wish list.
- Foster discussions within the community through a reply feature to comment on posts.
- Provide features to track user activity and game preferences through followers and wish lists.

## 3. ER Diagram
![jump drawio](https://github.com/user-attachments/assets/908947bb-f707-4676-88b2-f6fb94a5d1b3)

The following are the key features to be developed, based on the entity-relationship diagram:

- **Users**: Core entity representing registered users on the platform.
  - Has a unique identifier, user_id (Primary Key).
  - Can follow other users to build a network of followers.
  - Can create posts about games and reply to posts from other users.
  - --Can post reviews for game

- **Followers**: Each user has a list of followers, which allows for a networked social experience. Users can follow or unfollow each other.
  - Users can view their `follower_list` to see who is following them.
  - If the follow is one way, then the user who follow others are fans
  - If the following is mutual, then the two user are friends

- **Wish List**: Users can maintain a wish list of games they are interested in. This feature enhances user engagement by allowing them to bookmark games they wish to explore or purchase in the future.
  - Each User only has one wish list
  - Can be made visible to friends 

- **Game**: Central to the platform, games are the items around which most interactions occur. Users can add games to their wish lists and write posts related to specific games.
  - Has a unique identifier (game_id, platform_id)
  - Game can be on multiple platform
  - The application will maintain a catalog of games that users can interact with.

- **Posts**: Users can post content and share their thoughts on games. Other users can engage by replying to these posts, promoting community discussions.

- **Replies**: User can post reply to Post and Reply as well.

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


