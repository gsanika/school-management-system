# API Reference

## Authentication Endpoints

### Register User
```
POST /api/auth/register
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "password123",
  "role": "student",
  "fullName": "John Doe"
}

Response: 201 Created
{
  "message": "User registered successfully",
  "uid": "user-id"
}
```

### Login
```
POST /api/auth/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "password123"
}

Response: 200 OK
{
  "message": "Use Firebase Client SDK for authentication",
  "instruction": "Call signInWithEmailAndPassword on frontend"
}
```

### Get Current User
```
GET /api/auth/me
Authorization: Bearer TOKEN

Response: 200 OK
{
  "uid": "user-id",
  "email": "user@example.com",
  "role": "student",
  "fullName": "John Doe",
  "createdAt": "2024-01-01T00:00:00Z",
  "status": "active"
}
```

## Student Endpoints

### List All Students
```
GET /api/students
Authorization: Bearer TOKEN

Response: 200 OK
[
  {
    "id": "student-id",
    "enrollmentNumber": "STU001",
    "firstName": "John",
    "lastName": "Doe",
    "email": "john@example.com",
    "dateOfBirth": "2008-05-15",
    "classAssigned": "10-A",
    "status": "active"
  }
]
```

### Create Student
```
POST /api/students
Authorization: Bearer TOKEN
Content-Type: application/json

{
  "enrollmentNumber": "STU001",
  "firstName": "John",
  "lastName": "Doe",
  "email": "john@example.com",
  "dateOfBirth": "2008-05-15",
  "classAssigned": "10-A",
  "parentEmail": "parent@example.com",
  "parentPhone": "9876543210"
}

Response: 201 Created
```

### Get Student by ID
```
GET /api/students/:id
Authorization: Bearer TOKEN

Response: 200 OK
{
  "id": "student-id",
  "enrollmentNumber": "STU001",
  "firstName": "John",
  ...
}
```

### Update Student
```
PUT /api/students/:id
Authorization: Bearer TOKEN
Content-Type: application/json

{
  "firstName": "John",
  "lastName": "Doe",
  "classAssigned": "10-B"
}

Response: 200 OK
```

### Delete Student
```
DELETE /api/students/:id
Authorization: Bearer TOKEN

Response: 200 OK
{
  "message": "Student deleted successfully"
}
```

### Get Student Attendance
```
GET /api/students/:id/attendance
Authorization: Bearer TOKEN

Response: 200 OK
[
  {
    "id": "attendance-id",
    "studentId": "student-id",
    "date": "2024-01-15",
    "status": "present"
  }
]
```

## Grades Endpoints

### Create Grade
```
POST /api/grades
Authorization: Bearer TOKEN
Content-Type: application/json

{
  "studentId": "student-id",
  "courseId": "course-id",
  "marks": 95,
  "gradePoint": "A+",
  "semester": "1"
}

Response: 201 Created
```

### Get Student Grades
```
GET /api/grades/:studentId
Authorization: Bearer TOKEN

Response: 200 OK
[
  {
    "id": "grade-id",
    "studentId": "student-id",
    "courseId": "course-id",
    "marks": 95,
    "gradePoint": "A+"
  }
]
```

## Attendance Endpoints

### Mark Attendance
```
POST /api/attendance
Authorization: Bearer TOKEN
Content-Type: application/json

{
  "studentId": "student-id",
  "classId": "class-id",
  "date": "2024-01-15",
  "status": "present"
}

Response: 201 Created
```

### Get Student Attendance
```
GET /api/attendance/student/:studentId
Authorization: Bearer TOKEN

Response: 200 OK
[
  {
    "id": "attendance-id",
    "studentId": "student-id",
    "date": "2024-01-15",
    "status": "present"
  }
]
```

## Fees Endpoints

### Create Fee Record
```
POST /api/fees
Authorization: Bearer TOKEN
Content-Type: application/json

{
  "studentId": "student-id",
  "amount": 5000,
  "feeType": "tuition",
  "dueDate": "2024-02-01",
  "status": "pending"
}

Response: 201 Created
```

### Get Student Fees
```
GET /api/fees/student/:studentId
Authorization: Bearer TOKEN

Response: 200 OK
[
  {
    "id": "fee-id",
    "studentId": "student-id",
    "amount": 5000,
    "feeType": "tuition",
    "status": "pending"
  }
]
```

## Analytics Endpoints

### Dashboard Analytics
```
GET /api/analytics/dashboard
Authorization: Bearer TOKEN

Response: 200 OK
{
  "totalStudents": 1000,
  "totalTeachers": 50,
  "totalClasses": 40,
  "pendingFees": 15,
  "timestamp": "2024-01-15T10:30:00Z"
}
```

### Grades Analytics
```
GET /api/analytics/grades
Authorization: Bearer TOKEN

Response: 200 OK
{
  "totalRecords": 500,
  "averageMarks": "82.50",
  "timestamp": "2024-01-15T10:30:00Z"
}
```

### Attendance Analytics
```
GET /api/analytics/attendance
Authorization: Bearer TOKEN

Response: 200 OK
{
  "present": 950,
  "absent": 30,
  "leave": 20,
  "timestamp": "2024-01-15T10:30:00Z"
}
```

---

**All endpoints require authentication via Firebase Token in Authorization header**