# Step 1: Use the official Node.js image as the base image
FROM node:16-alpine

# Step 2: Set the working directory inside the container
WORKDIR /usr/src/app

# Step 3: Copy the index.js (and any other needed files) into the container
COPY index.js ./

# Step 4: Install required Node.js dependencies (e.g., express)
RUN npm install express

# Step 5: Expose the port that the application will run on (default port 3000 for Node.js apps)
EXPOSE 3000

# Step 6: Command to run the application
CMD ["node", "index.js"]
