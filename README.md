## API Booking Project Task

### Service List
- User
- Service
- Booking
- Transactions

---

### User

#### 1. Create a new user
- **Method**: `POST`
- **Endpoint**: `/register`
- **Request Body**:
    ```json
    {
      "name": "John Doe",
      "email": "john@example.com",
      "password": "password1234",
      "phone": "123456789",
      "address": "Depok",
    }
    ```
- **Response**:
    ```json
    {
      "statusCode": 201,
      "message": "Customer created successfully",
      "data": {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com",
        "password": "password1234",
        "phone": "123456789",
        "address": "Depok",
        "role": "customer"
      }
    }
    ```

#### role
- customer
- karyawan
- owner

#### 2. Get all user
- **Method**: `GET`
- **Endpoint**: `/users`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "User get successfully",
      "data": [
        {
            "id": 1,
            "name": "John Doe",
            "email": "john@example.com",
            "phone": "123456789",
            "address": "Depok",
            "role": "customer"
        }
      ]
    }

#### 3. Get a specific users by ID
- **Method**: `GET`
- **Endpoint**: `/users/:id`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Users get successfully",
      "data": {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com",
        "phone": "123456789",
        "address": "Depok",
        "role": "customer",
        "booking": [
            {
                "id": 1,
                "date": "2024-10-15",
                "time": "14:00",
                "status": "complete",
                "quantity": 2,
                "totalPrice": 300000,
                "service": {
                    "id": 1,
                    "name": "Cat Grooming",
                    "description": "Full grooming service",
                    "price": 150000
                }
            }
        ]
      }
    }
    ```

#### 4. Update a specific customer's information
- **Method**: `PATCH`
- **Endpoint**: `/users/:id`
- **Request Body**:
    ```json
    {
      "name": "John Doe Updated",
      "email": "john_updated@example.com"
    }
    ```
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Users updated successfully",
      "data": {
        "id": 1,
        "name": "John Doe Updated",
        "email": "john_updated@example.com",
        "phone": "123456789",
        "address": "Depok",
        "role": "customer",
      }
    }
    ```

#### 5. Delete a specific customer
- **Method**: `DELETE`
- **Endpoint**: `/users/:id`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Users deleted successfully",
    }
    ```

---

### Service

#### 1. Create a new service
- **Method**: `POST`
- **Endpoint**: `/services`
- **Request Body**:
    ```json
    {
      "name": "Cat Grooming",
      "description": "Full grooming service",
      "price": 150000
    }
    ```
- **Response**:
    ```json
    {
      "statusCode": 201,
      "message": "Service created successfully",
      "data": {
        "id": 1,
        "name": "Cat Grooming",
        "description": "Full grooming service",
        "price": 150000
      }
    }
    ```

#### 2. Get a specific service by ID
- **Method**: `GET`
- **Endpoint**: `/services/:id`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Service retrieved successfully",
      "data": {
        "id": 1,
        "name": "Cat Grooming",
        "description": "Full grooming service",
        "price": 150000
      }
    }
    ```

#### 2. Get a specific service by ID
- **Method**: `GET`
- **Endpoint**: `/services/:id`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Service get successfully",
      "data": {
        "id": 1,
        "name": "Cat Grooming",
        "description": "Full grooming service",
        "price": 150000
      }
    }
    ```

#### 3. Update a specific service's information
- **Method**: `PATCH`
- **Endpoint**: `/services/:id`
- **Request Body**:
    ```json
    {
      "name": "Cat Grooming Edit",
      "price": 175000
    }
    ```
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Service updated successfully",
      "data": {
        "id": 1,
        "name": "Cat Grooming",
        "description": "Full grooming service",
        "price": 175000
      }
    }
    ```

#### 4. Delete a specific service
- **Method**: `DELETE`
- **Endpoint**: `/services/:id`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Service deleted successfully",
    }
    ```

---

### Booking

untuk attribute status menggunakan ENUM berikut
- pending
- ongoing
- complete
- cancelled

## Alur Status Booking

Berikut adalah alur status yang digunakan:

1. **pending**  
   - **Deskripsi**: Booking telah dijadwalkan tetapi belum dimulai.

3. **ongoing**  
   - **Deskripsi**: Proses booking sedang berlangsung.

4. **complete**  
   - **Deskripsi**: Booking sudah selesai.

5. **cancelled**  
   - **Deskripsi**: Booking dibatalkan oleh pelanggan atau sistem.

---

#### 1. Create a new booking
- **Method**: `POST`
- **Endpoint**: `/bookings`
- **Request Body**:
    ```json
    {
      "serviceId": 1,
      "date": "2024-10-15",
      "time": "14:00",
      "quantity": 2
    }
    ```
- **Response**:
    ```json
    {
      "statusCode": 201,
      "message": "Booking created successfully",
      "data": {
        "id": 1,
        "userId": 1,
        "serviceId": 1,
        "date": "2024-10-15",
        "time": "14:00",
        "status": "pending",
        "quantity": 2,
        "totalPrice": 300000
      }
    }
    ```

#### 2. Get all booking
- **Method**: `GET`
- **Endpoint**: `/bookings`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Booking retrieved successfully",
      "data": [
        {
            "id": 1,
            "date": "2024-10-15",
            "time": "14:00",
            "status": "complete",
            "quantity": 2,
            "totalPrice": 300000,
            "user": {
                "id": 1,
                "name": "John Doe",
                "email": "john@example.com",
                "phone": "123456789",
                "address": "Depok"
            },
            "service": {
                "id": 1,
                "name": "Cat Grooming",
                "description": "Full grooming service",
                "price": 150000
            }
        }
      ]
    }
    ```


#### 3. Get a specific booking by ID
- **Method**: `GET`
- **Endpoint**: `/bookings/:id`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Booking retrieved successfully",
      "data": {
        "id": 1,
        "date": "2024-10-15",
        "time": "14:00",
        "status": "complete",
        "quantity": 2,
        "totalPrice": 300000,
        "user": {
            "id": 1,
            "name": "John Doe",
            "email": "john@example.com",
            "phone": "123456789",
            "address": "Depok"
        },
        "service": {
            "id": 1,
            "name": "Cat Grooming",
            "description": "Full grooming service",
            "price": 150000
        }
      }
    }
    ```

#### 4. Update a specific booking's information
- **Method**: `PATCH`
- **Endpoint**: `/bookings/:id`
- **Request Body**:
    ```json
    {
      "status": "ongoing",
      "quantity": 3,
      "totalPrice": 450000
    }
    ```
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Booking updated successfully",
      "data": {
        "id": 1,
        "date": "2024-10-15",
        "time": "14:00",
        "status": "ongoing",
        "quantity": 3,
        "totalPrice": 450000,
        "userId": 1,
        "serviceId": 1
      }
    }
    ```

#### 5. Delete a specific booking
- **Method**: `DELETE`
- **Endpoint**: `/bookings/:id`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Booking deleted successfully",
    }
    ```


### Transactions
#### 1. Create a new transactions
- **Method**: `POST`
- **Endpoint**: `/transactions`
- **Request Body**:
    ```json
    {
      "bookingId": 1,
      "payment": "cash",
    }
    ```
- **Response**:
    ```json
    {
      "statusCode": 201,
      "message": "Booking created successfully",
      "payment": "cash",
      "total": 450000,
      "booking": {
        "id": 1,
        "date": "2024-10-15",
        "status": "success",
        "quantity": 3,
        "totalPrice": 450000,
        "user": {
          "id": 1,
          "name": "John Doe",
          "email": "john@example.com",
          "phone": "123456789",
          "address": "Depok"
        },
        "service": {
          "id": 1,
          "name": "Cat Grooming",
          "description": "Full grooming service",
          "price": 150000
        }
      }
    }
    ```

#### 2. Get all transactions
- **Method**: `GET`
- **Endpoint**: `/transactions`
- **Response**:
    ```json
    {
      "data": [
        {
          "statusCode": 200,
          "message": "Booking get successfully",
          "payment": "cash",
          "total": 450000,
          "booking": {
            "id": 1,
            "date": "2024-10-15",
            "status": "success",
            "quantity": 3,
            "totalPrice": 450000,
            "user": {
              "id": 1,
              "name": "John Doe",
              "email": "john@example.com",
              "phone": "123456789",
              "address": "Depok"
            },
            "service": {
              "id": 1,
              "name": "Cat Grooming",
              "description": "Full grooming service",
              "price": 150000
            }
          }
        }
      ]
    }
    ```


#### 3. Get a specific booking by ID
- **Method**: `GET`
- **Endpoint**: `/bookings/:id`
- **Response**:
    ```json
    {
      "statusCode": 201,
      "message": "Transactions get successfully",
      "payment": "cash",
      "total": 450000,
      "booking": {
        "id": 1,
        "date": "2024-10-15",
        "status": "success",
        "quantity": 3,
        "totalPrice": 450000,
        "user": {
          "id": 1,
          "name": "John Doe",
          "email": "john@example.com",
          "phone": "123456789",
          "address": "Depok"
        },
        "service": {
          "id": 1,
          "name": "Cat Grooming",
          "description": "Full grooming service",
          "price": 150000
        }
      }
    }
    ```