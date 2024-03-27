# Use an official Go runtime as the base image
FROM golang:1.19

# Set the working directory in the container
WORKDIR /app

# Copy the Go modules manifests
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy the rest of the application code to the container
COPY . .

# Build the Go app
RUN go build -o main .

# Expose the port your app runs on
EXPOSE 8080

# Command to run your application
CMD ["./main"]
