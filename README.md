## API Booking Project Task


Tabel Booking
![Booking ERD](booking-erd.png)

### Service List
- User
- Service
- Booking
- Transactions

---

### User

#### 1. Create a new User
- **Method**: `POST`
- **Endpoint**: `/register`
- **Request Body**: form

| Field     | Value           |
|-----------|-----------------|
| `name`    | John Doe        |
| `email`   | john@example.com|
| `password`| password1234    |
| `phone`   | 08123456789     |
| `address` | Depok           |
| `photo`   | file image.png  |

<!-- #### 1. Create a new User
- **Method**: `POST`
- **Endpoint**: `/register`
- **Request Body**:
    ```json
    {
      "name": "John Doe",
      "email": "john@example.com",
      "password": "password1234",
      "phone": "08123456789",
      "address": "Depok",
      "photo": "image",
    }
    ``` -->
- **Response**:
    ```json
    {
      "statusCode": 201,
      "message": "User registered successfully",
      "data": {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com",
        "password":"$2a$12$EFxeeANU8By4ktMHNjhoyeWXW46F4iozJqUFuJ0N8Rho7OreL.Y9i",
        "phone": "08123456789",
        "address": "Depok",
        "photo": "image.png",
        "role": "customer"
      }
    }
    ```

#### 2. Login User
- **Method**: `POST`
- **Endpoint**: `/login`
- **Request Body**:
    ```json
    {
      "email": "john@example.com",
      "password": "password1234"
    }
    ```
- **Response**:
    ```json
    {
      "statusCode": 201,
      "message": "User login successfully",
      "data": {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com",
        "phone": "08123456789",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
      }
    }
    ```

#### role
- customer
- karyawan

#### 3. Get all user
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
            "phone": "08123456789",
            "address": "Depok",
            "photo": "http://localhost:8000/uploads/image.png",
            "role": "customer"
        }
      ]
    }

#### 4. Get a specific users by ID
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
        "phone": "08123456789",
        "address": "Depok",
        "photo": "http://localhost:8000/uploads/image.png",
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

#### 5. Update a specific users information
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
        "phone": "08123456789",
        "address": "Depok",
        "photo": "http://localhost:8000/uploads/image.png",
        "role": "customer",
      }
    }
    ```

#### 6. Delete a specific customer
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

#### 3. Get a specific service by ID
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

#### 4. Update a specific service's information
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

#### 5. Delete a specific service
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
- upcoming
- ongoing
- complete
- cancelled

## Alur Status Booking

Berikut adalah alur status yang digunakan:

1. **pending**  
   - **Deskripsi**: Booking belum melakukan pembayaran.
2. **upcoming**  
   - **Deskripsi**: Booking telah berhasil dibayar dan sedang menunggu waktu booking.

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
- **Request Header**:
    - `Authorization`: `Bearer <token>`
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
        "quantity": 2,
        "totalPrice": 300000,
        "status": "pending"
      }
    }
    ```

### keterngan buat booking
- Saat menyimpan booking, perlu dilakukan `pengecekan tanggal dan waktu` pada tabel booking.
- Jika tanggal dan waktu yang diinputkan sudah ada di tabel booking, berikan respons dengan `statusCode 400`, dengan pesan "Tanggal atau waktu sudah terisi, silakan masukkan tanggal dan waktu yang lain."

#### 2. Get all booking
- **Method**: `GET`
- **Endpoint**: `/bookings`
- **Request Header**:
    - `Authorization`: `Bearer <token>`
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
                "phone": "08123456789",
                "address": "Depok",
                "photo": "http://localhost:8000/uploads/image.png"

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
- **Request Header**:
    - `Authorization`: `Bearer <token>`
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
            "phone": "08123456789",
            "address": "Depok",
            "photo": "http://localhost:8000/uploads/image.png"

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
- **Request Header**:
    - `Authorization`: `Bearer <token>`
- **Request Body**:
    ```json
    {
      "status": "ongoing",
      "quantity": 3,
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
- **Request Header**:
    - `Authorization`: `Bearer <token>`
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
- **Request Header**:
    - `Authorization`: `Bearer <token>`
- **Request Body**: form

    | Field      | Value             |
    |------------|-------------------|
    | `bookingId`| 1                 |
    | `payment`  | transfer          |
    | `receipt`  | file transfer.png |

- **Response**:
    ```json
    {
      "bookingId": 1,
      "payment": "transfer",
      "receipt": "transfer.png",
      "transactionDate": "2024-10-15 10:55",
      "status": "pending"
    }
    ```
### ket
- untuk transactionDate isi dengan new Date ketika create transaction
- status buatkan `enum ('pending','succcess','failed')` default pending
- ketika transaction berhasil `ubah status booking` yang tadinya `pending menjadi upcoming`
- payment buatkan `enum ('transfer','wallet')`

#### 2. Get all transactions
- **Method**: `GET`
- **Endpoint**: `/transactions`
- **Request Header**:
    - `Authorization`: `Bearer <token>`
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
          },
          "user": {
            "id": 1,
            "name": "John Doe",
            "email": "john@example.com",
            "phone": "08123456789",
            "address": "Depok",
            "photo": "http://localhost:8000/uploads/image.png"
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


#### 3. Get a specific transactions by ID
- **Method**: `GET`
- **Endpoint**: `/transactions/:id`
- **Request Header**:
    - `Authorization`: `Bearer <token>`
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Transactions get successfully",
      "payment": "cash",
      "total": 450000,
      "booking": {
        "id": 1,
        "date": "2024-10-15",
        "status": "success",
        "quantity": 3,
        "totalPrice": 450000,
      },
      "user": {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com",
        "phone": "08123456789",
        "address": "Depok",
        "photo": "http://localhost:8000/uploads/image.png"
      },
      "service": {
        "id": 1,
        "name": "Cat Grooming",
        "description": "Full grooming service",
        "price": 150000
      }
    }
    ```

#### 4. Update a specific transactions information
- **Method**: `PATCH`
- **Endpoint**: `/transactions/:id`
- **Request Header**:
    - `Authorization`: `Bearer <token>`
- **Request Body**:
    ```json
    {
      "status": "success",
    }
    ```
- **Response**:
    ```json
    {
      "statusCode": 200,
      "message": "Transactions update successfully",
      "bookingId": 1,
      "payment": "transfer",
      "receipt": "transfer.png",
      "transactionDate": "2024-10-15 10:55",
      "status": "success"
    }
    ```