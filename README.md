# graphqlNode

POC to use GraphQL with Apollo, prisma, postgres and nodejs.

Run local docker postgres, and create tables for User and Post.

```
-- Enable pgcrypto extension for gen_random_uuid function
CREATE EXTENSION IF NOT EXISTS "pgcrypto";

-- Create User table
CREATE TABLE "User" (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    username VARCHAR(255),
    CONSTRAINT "User_email_unique" UNIQUE (email)
);

-- Create Post table
CREATE TABLE "Post" (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    authorId UUID NOT NULL,
    CONSTRAINT "Post_authorId_fkey" FOREIGN KEY (authorId) REFERENCES "User" (id)
);

-- Insert one user
INSERT INTO "User" (email, username)
VALUES ('user@example.com', 'username123');

```
