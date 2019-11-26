FROM node:latest

## How an image is built
# Set environment variables
ENV APP_ROOT=/app
ENV APP_PORT=3000
ENV DB_HOST=localhost

# Create the directory and cd into it
WORKDIR ${APP_ROOT}

# Copy files into the image
# Files will be copied into /app
ADD main.js .
ADD package.json .
ADD public public
ADD views views
ADD config config

# Run some command (at image build time)
RUN npm install

## How an image is provisioned/run
# What port our container will be exposing
EXPOSE ${APP_PORT}

# Add heathcheck to the application
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD  curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

# node main.js
ENTRYPOINT ["node", "main.js"]

CMD [""]