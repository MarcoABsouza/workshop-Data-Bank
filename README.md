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


## Data entry

Fictitious data was inserted into all the tables to simulate a working workshop environment. The data includes information on customers, vehicles, services, service orders, materials.

## Consultations held

Several queries were carried out to demonstrate the database's functionalities. Some queries include:

1.  how many customers the workshop has served so far?

"	

	select count(c.id_client) as Clientes_Atendidos
 	from clients as c;	
 

2. What is the total amount billed by the workshop in a given period?


"

	select sum(s.price_service) as total_faturado
	from order_services as os
	right join services as s on s.id_services = os.service_order;	


3. What are the services most requested by customers?

"

	SELECT s.name_service, COUNT(*) AS Quantidade
	FROM order_services os
	right join services s ON os.service_order = s.id_services
	GROUP BY s.name_service
	ORDER BY Quantidade DESC;	
 
4. Which employees performed the most services in the last month?

"
	
	select emp.name_employee, count(*) as quantidade_de_serviços
	from employees emp
	left join order_services as os on emp.id_employees = os.employee_service
	group by emp.name_employee
	order by quantidade_de_serviços;
 
5. What are the current open work orders?

"

	select date_order as Data_Inicial_do_Serviço,status_order as Status_Serviço
	from order_services
	where status_order="Em andamento";

These queries are just examples of how the database can be consulted to obtain useful information for managing e-commerce.



