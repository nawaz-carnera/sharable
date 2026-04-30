# ENTITIES and ATTRIBUTES

### Branch

- branch_id int (primary key)
- name varchar(255)
- state varchar(255)
- city varchar(255) (Texas, New York, etc.)
- phone_number varchar(255)
- created_at timestamp
- updated_at timestamp

### Member

- member_id int (primary key)
- branch_id int (foreign key)
- name varchar(255)
- email varchar(255)
- phone_number varchar(255)
- status
- dob date
- joined_at timestamp
- left_at timestamp

### Trainer

- trainer_id int (primary key)
- branch_id int (foreign key)
- name varchar(255)
- email varchar(255)
- phone_number varchar(255)
- specialization varchar(255)
- created_at timestamp
- updated_at timestamp

### MembershipPlan (the template — no member_id!)

- plan_id (PK)
- name (e.g., "Gold Monthly")
- type ENUM (monthly, yearly)
- price decimal(10,2)
- duration_days int
- created_at timestamp
- updated_at timestamp

### Membership (the subscription instance — this is the join table)

- membership_id (PK)
- member_id (FK → Member)
- plan_id (FK → MembershipPlan)
- start_date
- end_date
- status (active, expired, cancelled)
- created_at timestamp
- updated_at timestamp

### Class

- class_id int (primary key)
- branch_id int (foreign key)
- name varchar(255)
- schedule varchar(255)
- created_at timestamp
- updated_at timestamp

### Equipment

- equipment_id int (primary key)
- branch_id int (foreign key)
- name varchar(255)
- type varchar(255)
- quantity int
- created_at timestamp
- updated_at timestamp

### Payment

- payment_id int (primary key)
- member_id int (foreign key)
- branch_id int (foreign key) // <- to track revenues by branch>
- personal_training_session_id int (foreign key, nullable)
- amount decimal(10, 2)
- date date
- paid_at time
- created_at timestamp
- updated_at timestamp

### PersonalTrainingSession

- session_id (PK)
- trainer_id (FK)
- member_id (FK)
- mode ENUM ('in_person', 'virtual')
- branch_id (FK, nullable) ← only filled for in_person
- meeting_link varchar(500) (nullable) ← only filled for virtual
- platform varchar(50) (nullable) ← only filled for virtual (zoom, meet, etc.)
- session_date timestamp
- duration int
- status varchar (scheduled, completed, cancelled, no_show)

### ClassBooking

- booking_id int (primary key)
- member_id int (foreign key)
- class_id int (foreign key)
- date date
- time time
- status varchar(255)
- created_at timestamp
- updated_at timestamp

# RELATIONSHIP

- Branch -> One has many -> Member
- Member -> Many has Many -> Class
- Trainer -> One has Many -> Specialization
- Trainer -> One has Many -> PersionalTrainingSession
- Member -> One has Many -> PersonalTrainingSession
- Member -> Many has Many -> MembershipPlan
- Branch -> One has Many - Equipment
- Member -> One has Many -> Payment
- Class -> Many has Many -> Member (Join Table ClassBooking)
