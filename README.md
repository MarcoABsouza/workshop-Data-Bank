# Database for Workshop

This project consists of creating a database for an e-commerce system using MySQL. The database is designed to store information about customers, vehicles, services, service orders
,materials,employees as well as managing the relationship between these entities.

## Model Database ER
<img src="workshop.png" alt="relational database schema">

## Database Model
The database model consists of seven main tables:

1. **customers**: Stores customers personal information, such as name, phone,cpf,address.
2. **employees**: Stores employees information name,salary,office
3. **vehicles**: Stores vehicle information, such as model and plate.
4. **services**: Stores information about services, such as description problem,name service and price.
5. **service orders**: Stores information about service orders, such as date and status.
6. **materials**: stores information about name material, quantity and price.

## Creation Data Base comands

"""

   create table clients (
	id_client int not null auto_increment,
    client_name varchar(100) not null,
    phone varchar(20) not null,
    cpf char(11) not null,
    address varchar(255),
    constraint unique_client_cpf unique (cpf),
    constraint pk_client primary key (id_client)
);
create table vehicle (
	id_vehicle int not null auto_increment,
    model_vehicle varchar(100) not null,
    plate_vehicle char(7) not null,
    client_vehicle int,
    constraint unique_plate_vehicle unique (plate_vehicle),
    constraint pk_vehicle primary key (id_vehicle),
    constraint fk_client foreign key (client_vehicle) references clients (id_client)
);

create table services (
	id_services int not null auto_increment,
    description_problem varchar(255) not null,
    name_service varchar(45),
    price_service decimal(10,2) not null,
    constraint pk_service primary key (id_services)
);

create table employees (
	id_employees int not null auto_increment,
    name_employee varchar(100) not null,
    salary decimal(10,2) not null,
    office varchar(45),
    constraint pk_employee primary key (id_employees)
);

create table order_services (
	id_order int not null auto_increment,
    date_order date not null,
    status_order varchar(50) not null,
    vehicle_client int,
    employee_service int,
    service_order int,
    constraint pk_order primary key (id_order),
    constraint fk_vehicle_client foreign key (vehicle_client) references vehicle (id_vehicle),
    constraint fk_employee_works_On foreign key (employee_service) references employees (id_employees),
    constraint fk_service_order foreign key (service_order) references services (id_services)
);

create table material_service (
	id_material int not null auto_increment,
    name_material varchar(50) not null,
    quantity int default 0,
    price_material float not null,
    services int,
    constraint pk_material primary key (id_material),
    constraint fk_services foreign key (services) references services (id_services)
);


"""

## Data entry

Fictitious data was inserted into all the tables to simulate a working workshop environment. The data includes information on customers, vehicles, services, service orders, materials.

## Consultations held

Several queries were carried out to demonstrate the database's functionalities. Some queries include:

1. Which product did each customer buy.

"""

   

"""

2. Where does each client live.

"""

    t;

"""

3. How many orders were placed by each customer.


"""

    
    
"""

4. List of product suppliers and stocks.

"""

   
"""

These queries are just examples of how the database can be consulted to obtain useful information for managing e-commerce.



