# Description: Dockerfile for the Client/frontend side of the side of the MERN Stack Application

# Stage 1: Install dependencies
# Used the official node image as the parent image 
FROM node:18.9.1 AS deps

# Sets the working directory 
WORKDIR /app

# Copy the dependencies file from host to the image working directory
COPY package.json package-lock.json ./ 

# Runs the command to install dependencies inside your image
RUN --mount=type=cache,target=/root/.npm \
	npm ci


# Stage 2: run dev server
FROM node:18.9.1

WORKDIR /app

# Copy installed dependencies from stage 1
COPY --from=deps /app/node_modules ./node_modules

# Informs Docker that the container will be listening on the specified port at runtime 
EXPOSE 5173

# Copies the rest of the  app's source code from the host to the image filesystem
COPY . . 

# Runs the specified  command within the image to start the container application
CMD ["npm", "run", "dev"]
