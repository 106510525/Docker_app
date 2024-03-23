# Use a Golang base image
FROM golang:latest as builder

# Set the working directory in the container
WORKDIR /app

# Copy the Go module files to the container
COPY go.mod .
COPY go.sum .

# Install dependencies
RUN go mod download

# Copy the remaining application source code to the container
COPY . .

# Build the application
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

# Use a minimal base image for the final container
FROM alpine:latest

# Set the working directory in the container
WORKDIR /app

# Copy the executable built in the previous stage to the final container
COPY --from=builder /app/app .

# Expose port 8080
EXPOSE 8080

# Command to run the backend application
CMD ["./app"]

