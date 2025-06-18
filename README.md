# Database Schema Documentation

## Tables Structure

### 1. DEPARTMENT Table
| Column Name       | Data Type     | Constraints               | Description                     |
|-------------------|---------------|---------------------------|---------------------------------|
| DNum             | INT           | PRIMARY KEY, NOT NULL     | Department number               |
| DName            | VARCHAR(50)   | NOT NULL, UNIQUE          | Department name                 |
| Manager_SSN      | CHAR(11)      | NOT NULL, FOREIGN KEY     | Manager's SSN (references EMPLOYEE) |
| Manager_Hire_Date| DATE          |                           | Date manager was appointed      |


---

### 2. EMPLOYEE Table
| Column Name       | Data Type     | Constraints               | Description                     |
|-------------------|---------------|---------------------------|---------------------------------|
| SSN              | CHAR(11)      | PRIMARY KEY, NOT NULL     | Employee's social security number |
| Pname            | VARCHAR(50)   | NOT NULL                  | Employee's first name           |
| Lname            | VARCHAR(50)   | NOT NULL                  | Employee's last name            |
| Birth_Date       | DATE          |                           | Employee's birth date           |
| Gender           | CHAR(1)       | CHECK (M/F)             | Employee's gender               |
| Supervisor_SSN   | CHAR(11)      | FOREIGN KEY, NULL         | Supervisor's SSN (self-reference) |
| DNum             | INT           | NOT NULL, FOREIGN KEY     | Department number               |
| Hire_Date        | DATE          | NOT NULL                  | Employee hire date              |


---

### 3. DEVELOPER Table
| Column Name       | Data Type     | Constraints               | Description                     |
|-------------------|---------------|---------------------------|---------------------------------|
| Employee_SSN     | CHAR(11)      | PRIMARY KEY, FOREIGN KEY, NOT NULL | Employee's SSN |
| Dependent_Name   | VARCHAR(50)   | PRIMARY KEY, NOT NULL     | Dependent's name                |
| Gender           | CHAR(1)       | CHECK (M/F)             | Dependent's gender              |
| Birth_Date       | DATE          |                           | Dependent's birth date          |


---

### 4. PROJECT Table
| Column Name       | Data Type     | Constraints               | Description                     |
|-------------------|---------------|---------------------------|---------------------------------|
| PNumber          | INT           | PRIMARY KEY, NOT NULL     | Project number                  |
| PName            | VARCHAR(50)   | NOT NULL, UNIQUE          | Project name                    |
| Location         | VARCHAR(100)  |                           | Project location                |
| City             | VARCHAR(50)   |                           | Project city                    |
| DNum             | INT           | NOT NULL, FOREIGN KEY     | Department number               |

---

### 5. WORKS_ON Table
| Column Name       | Data Type     | Constraints               | Description                     |
|-------------------|---------------|---------------------------|---------------------------------|
| Employee_SSN     | CHAR(11)      | PRIMARY KEY, FOREIGN KEY, NOT NULL | Employee's SSN |
| PNumber          | INT           | PRIMARY KEY, FOREIGN KEY, NOT NULL | Project number |
| Hours            | DECIMAL(5,2)  | CHECK (>= 0)              | Hours worked on project         |

---

## Relationships

1. **Department-Manager (1:1)**
2. **Employee-Department (N:1)**
3. **Employee-Supervisor (1:N)**
4. **Department-Project (1:N)**
5. **Employee-Project (M:N)**
6. **Employee-Developer (1:N)**
   


