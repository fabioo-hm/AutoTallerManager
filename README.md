# Examen ef- David Santiago Lopez Castillo🚗⚙

crear usuario con rol de amdin para poder crear las piezas
```
POST http://localhost:5104/api/auth/register

{
	"username": "campuslands",
	"password" : "1234",
	"email":"campuslands@gmail.com",
	"role": "admin"
}
```
Ingresar con el rol previamente creado
```
POST http://localhost:5104/api/auth/login

{
	"username": "campuslands",
	"password" : "1234",
}
```

Crear los repuestos
```
POST http://localhost:5104/api/spareparts

{
	"code": "123",
	"description" : "refrigerante",
	"stockquantity": 3,
	"unitprice": 12.99
}

{
	"code": "124",
	"description" : "aceite 55w",
	"stockquantity": 1,
	"unitprice": 20.00
}

{
	"code": "125",
	"description" : "plumillas para parabrisas",
	"stockquantity": 0,
	"unitprice": 5.00
}

{
	"code": "126",
	"description" : "llantas",
	"stockquantity": 10,
	"unitprice": 50.00
}

{
	"code": "127",
	"description" : "tapetes",
	"stockquantity": 8,
	"unitprice": 13.00
}

```

Solicitar los datos ingresados
```
GET http://localhost:5104/api/spareparts

select * from spare_parts;
```
