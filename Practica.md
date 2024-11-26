# Actividad concesionarios.

Crear la bbdd y usarla:

```sql
create database concesionarios;
use concesionarios;
```

Crear las tablas *tiendas* y *vehiculos*.

```sql
create table tiendas (
    id int not null,
    nombre varchar(50) not null,
    ciudad varchar(50) not null,
    numerotrabajadores int not null,
    superficie int not null,
    primary key (id)
);
create table vehiculos (
    matricula varchar(50) not null,
    marca varchar(50) not null,
    modelo varchar(50) not null,
    color varchar(50) not null,
    cilindrada int not null,
    antiguedad year not null,
    kilometros int not null,
    precio int not null,
    idtienda int not null,
    foreign key(idtienda) references tiendas(id)
);
```

Insertar valores en las tablas *vehiculos* y *tiendas*.

```sql
insert into tiendas (
        id,
        nombre,
        ciudad,
        numerotrabajadores,
        superficie
)
values 
    (1, 'auto 2', 'madrid', 5, 1250),
    (2, 'multimarcatotal', 'madrid', 5, 1750),
    (3, 'carauto', 'madrid', 10, 2000),
    (4, 'turismos diaz', 'barcelona', 5, 1000),
    (5, 'barna car', 'barcelona', 15, 3000);

insert into vehiculos (
    matricula,
    marca,
    modelo,
    color,
    cilindrada,
    antiguedad,
    kilometros,
    precio,
    idtienda
)
values 
    ('1213-CRX', 'Seat', 'León', 'Negro', 1.8, 2004, 180000, 2000, 1),
    ('3243-HTN', 'Seat', 'Altea', 'Rojo', 1.2, 2013, 85000, 7900, 2),
    ('6643-KBM', 'Seat', 'Ibiza', 'Blanco', 1.0, 2017, 25000, 10900, 2),
    ('8265-HZL', 'Nissan', 'Juke', 'Blanco', 1.6, 2014, 110000, 13900, 3),
    ('8919-HHH', 'Nissan', 'Qashqai', 'Gris', 2.0, 2011, 200000, 8500, 4),
    ('7623-GRS', 'Volkswagen', 'Tiguan', 'Gris', 2.0, 2010, 130000, 12000, 1),
    ('4901-KPS', 'Volkswagen', 'Polo', 'Azul', 1.0, 2018, 10000, 11500, 2),
    ('6841-LBN', 'Volkswagen', 'Golf', 'Rojo', 1.6, 2019, 15000, 22500, 1);
```

## Realiza las siguientes consultas:

1. Consulta que muestre todas las tiendas de más de 1500 metros, ordenadas por el nombre de la tienda.

```sql
select * from tiendas
where superficie >= 1500 order by nombre;
```

2. Consulta que muestre la marca y el modelo de los vehículos que sean blancos su antigüedad sea inferior a 2012.

```sql
select * from vehiculos
where color = 'blanco' and antiguedad <= 2012;
```

3. Consulta que muestre el nombre de la tienda, la marca, el modelo y el precio del vehículo.

```sql
select * from vehiculos;
```

4. ¿Cuántos vehículos tenemos de cada marca?

```sql
select count(marca) as cantidad, marca from vehiculos
group by marca order by marca;
```
