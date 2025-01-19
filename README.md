
# E-Commerce Web Application with Microservices (Backend)

This repository contains the backend components of an E-Commerce Web Application that uses 5-6 interconnected microservices, orchestrated with Docker Compose. The backend handles various services like product management, user authentication, order processing, and payment processing. The microservices communicate via REST APIs and are built using Python, Node.js, and other necessary technologies.

## Project Structure

- `api-gateway/`: Acts as the entry point for all API requests and routes them to appropriate services.
- `auth-service/`: Handles user authentication and authorization (login, registration, token generation).
- `product-service/`: Manages product-related operations (CRUD operations on products).
- `order-service/`: Handles order-related operations (placing and managing orders).
- `payment-service/`: Manages payment processing (order payment).
- `docker-compose.yml`: Orchestrates all services and defines their respective containers.
  
## Technologies Used

- **Backend Services**:
  - Python (Flask/Django) or Node.js (Express)
  - Docker
  - PostgreSQL/MySQL (or other relational databases)
  - Redis (Optional for caching)
  - JWT (JSON Web Token) for authentication

- **Development Tools**:
  - Docker Compose for multi-container orchestration
  - Alpine base images (`python:alpine`, `node:alpine`) for lightweight containers

## Getting Started

To run this project locally, you'll need to have Docker and Docker Compose installed. Follow the steps below:

### Prerequisites

- Install [Docker](https://www.docker.com/get-started)
- Install [Docker Compose](https://docs.docker.com/compose/install/)

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/ecommerce-microservices-backend.git
   cd ecommerce-microservices-backend
   ```

2. Build and run the services using Docker Compose:

   ```bash
   docker-compose up --build
   ```

3. After a successful build, the backend services will be available at:

   - API Gateway: `http://localhost:8080`
   - Authentication Service: `http://localhost:5000`
   - Product Service: `http://localhost:5001`
   - Order Service: `http://localhost:5002`
   - Payment Service: `http://localhost:5003`

### API Documentation

Each microservice exposes a set of RESTful APIs. You can interact with these APIs for CRUD operations, authentication, and payment handling. Here's a quick guide to the available endpoints:

#### Authentication Service (`auth-service`)

- **POST /auth/login**: User login, returns a JWT token.
- **POST /auth/register**: User registration, creates a new user.

#### Product Service (`product-service`)

- **GET /products**: Get a list of all products.
- **GET /products/{id}**: Get details of a specific product.
- **POST /products**: Add a new product (admin only).
- **PUT /products/{id}**: Update product details (admin only).
- **DELETE /products/{id}**: Delete a product (admin only).

#### Order Service (`order-service`)

- **POST /orders**: Place a new order.
- **GET /orders/{id}**: Get order details by order ID.
- **PUT /orders/{id}**: Update order status (e.g., shipped, delivered).
- **GET /orders**: Get a list of orders for a user.

#### Payment Service (`payment-service`)

- **POST /payments**: Process payment for an order.
- **GET /payments/{orderId}**: Get payment status for a specific order.

## Docker Compose Overview

The `docker-compose.yml` file defines the following services:

- **api-gateway**: Routes requests to appropriate microservices.
- **auth-service**: Manages user authentication and authorization.
- **product-service**: Handles product management.
- **order-service**: Manages orders and order status.
- **payment-service**: Handles payment processing.

Each service is containerized and linked using Docker Compose, allowing you to spin up the entire system with a single command.

## Testing the Application

1. Once the containers are running, you can test the APIs using any API testing tool like Postman or cURL.
2. Use JWT tokens for authentication (login via `/auth/login`).
3. Send requests to each service according to the available endpoints mentioned above.

## Notes

- Make sure you have PostgreSQL or MySQL running, as required by your microservices.
- You can scale individual services or add new ones by modifying the `docker-compose.yml` file.

## Future Improvements

- Add logging for better error tracking and debugging.
- Implement rate-limiting and security features.
- Enhance service intercommunication with Kafka or RabbitMQ for asynchronous messaging.

## Contributing

If you'd like to contribute to this project, feel free to fork the repository, create a branch for your feature/bug fix, and submit a pull request. Ensure that all tests pass before submitting.

