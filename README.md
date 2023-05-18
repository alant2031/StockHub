# StockHub

The StockHub is a RESTful API that allows you to manage products in an inventory system. It provides CRUD operations for creating, reading, updating, and deleting products. Additionally, it includes authentication and authorization mechanisms to secure access to the API endpoints.

## API Endpoints

The Product Inventory API exposes the following endpoints:

-   `GET /products`: Retrieve all products.
-   `GET /products/:id`: Retrieve a specific product by ID.
-   `POST /products`: Create a new product.
-   `PUT /products/:id`: Update a specific product by ID.
-   `DELETE /products/:id`: Delete a specific product by ID.

## Authentication and Authorization

The API uses token-based authentication using JSON Web Tokens (JWT). To access the protected endpoints, you need to include the JWT token in the Authorization header of your requests using the Bearer scheme.

To authenticate and obtain a token:

1. Send a `POST` request to `/auth/login` with the following payload:

    ```
    {
      "username": "james",
      "email": "james@email.com",
      "password": "abc123",
      "admin": false
    }
    ```

2. The API will respond with a JWT token.
3. Include the token in subsequent requests by adding an `Authorization` header:

    ```
    Authorization: Bearer <token>
    ```

    Replace `<token>` with the actual token value obtained from the login response.

The API implements role-based authorization as follows:

-   Admin: Users with the "admin" role have full access to all API endpoints, including creating, updating, and deleting all products.
-   User: Users with the "user" role have read-only access to the /products endpoints, allowing them to retrieve product information but not modify it.

Ensure that you assign appropriate roles to users when creating or updating their profiles. The API will validate the role during authorization checks on the protected endpoints.
