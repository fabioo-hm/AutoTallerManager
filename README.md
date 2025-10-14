# AutoTallerManager - Sistema de Gestión para Talleres Automotrices 🚗⚙

## Descripción
AutoTallerManager es un backend RESTful desarrollado en ASP.NET Core que implementa una solución integral para la gestión de talleres automotrices. La aplicación permite centralizar y automatizar procesos clave como la gestión de clientes, vehículos, órdenes de servicio, repuestos y facturación, garantizando la trazabilidad de cada actividad y optimizando el flujo de trabajo de mecánicos, recepcionistas y administradores.

## Arquitectura del Proyecto

### Patrones de Diseño Implementados
- **Hexagonal Architecture (Ports & Adapters)**: Separación clara entre capas de negocio e infraestructura
- **Repository Pattern**: Para acceso a datos con abstracción de persistencia
- **Unit of Work Pattern**: Para transacciones atómicas y consistencia de datos
- **DTO Pattern**: Para transferencia de datos entre capas
- **Dependency Injection**: Para inversión de control y desacoplamiento
- **Generic Repository**: Para operaciones CRUD reutilizables

### Estructura
```
AutoTallerManager/
│
├── Api/ 
│ ├── Controllers/
│       ├── AuthController.cs
│       ├── BaseApiController.cs
│       ├── CustomersController.cs
│       ├── InvoicesController.cs
│       ├── OrderDetailsController.cs
│       ├── ServiceOrdersController.cs
│       ├── SparepartsController.cs
│       ├── VehiclesController.cs
│       ├── WeatherForecastController.cs
│ ├── Dtos/
│       ├──Auth/
│           ├── AddRoleDto.cs
│           ├── DataUserDto.cs
│           ├── LoginDto.cs
│           ├── RefreshTokenRequestDto.cs
│           ├── RegisterDto.cs
│           ├── UpdateUserDto.cs
│           ├── UserListDto.cs
│       ├──Customers/
│           ├── CreateCustomerDto.cs
│           ├── CustomerDto.cs
│           ├── UpdateCustomerDto.cs
│       ├──Invoices/
│           ├── CreateInvoiceDto.cs
│           ├── InvoiceDto.cs
│           ├── UpdateInvoiceDto.cs
│       ├──OrderDertails/
│           ├── CreateOrderDetailDto.cs
│           ├── OrderDetailDto.cs
│           ├── UpdateOrderDetailDto.cs
│       ├──ServiceOrders/
│           ├── CreateServiceOrderDto.cs
│           ├── ServiceOrderDto.cs
│           ├── UpdateServiceOrderDto.cs
│           ├── UpdateServiceOrderStatusDto.cs
│       ├──SpareParts/
│           ├── CreateSparePartDto.cs
│           ├── SparePartDto.cs
│           ├── UpdateSparePartDto.cs
│       ├──Vehicles/
│           ├── CreateVehicleDto.cs
│           ├── VehicleDto.cs
│           ├── UpdateVehicleDto.cs   
│ ├── Extensions/
│       ├── ApplicaationServiceExtensions.cs
│       ├── DbSeederExtensions.cs
│ ├── Helpers/
│       ├──Errors/
│           ├── ApiException.cs
│           ├── ApiResponse.cs
│           ├── ApiValidation.cs
│           ├── ExceptionMiddleware.cs
│       ├── JWT.cs
│       ├── Pages.cs
│       ├── Params.cs
│       ├── UserAuthorization.cs
│ ├── Mappings/
│       ├── CustomerProfile.cs
│       ├── InvoiceProfile.cs
│       ├── OrderDetailProfile.cs
│       ├── ServiceOrderProfile.cs
│       ├── SparePartProfile.cs
│       ├── VehicleProfile.cs
│ ├── Properties/
│       ├── launchSettings.cs
│ ├── Services/
│       ├── IUserService.cs
│       ├── UserService.cs
│ ├── .dockerignore
│ ├── Api.csproj
│ ├── Program.cs
│ ├── appsettings.Development.json
│ ├── appsettings.json
│
│
├── Application/
│ ├── Abtractions/
│       ├──Auth/
│           ├── IRefreshTokenService.cs
│           ├── IRolService.cs
│           ├── IUserMemberRolService.cs
│           ├── IUserMemberService.cs
│       ├── ICustomerRepository.cs
│       ├── IInvoiceRepository.cs
│       ├── IOrderDetailRepository.cs
│       ├── IServiceOrderRepository.cs
│       ├── ISparePartRepository.cs
│       ├── IUnitOfWork.cs
│       ├── IVehicleRepository.cs
│ ├── Customers/
│       ├── CreateCustomer.cs
│       ├── CreateCustomerHandler.cs
│ ├── Invoices/
│       ├── CreateInvoice.cs
│       ├── CreateInvoiceHandler.cs
│ ├── OrderDetails/
│       ├── CreateOrderDetail.cs
│       ├── CreateOrderDetailHandler.cs
│ ├── ServiceOrders/
│       ├── CreateServiceOrder.cs
│       ├── CreateServiceOrderHandler.cs
│ ├── SpareParts/
│       ├── CreateSparePart.cs
│       ├── CreateSparePartHandler.cs
│ ├── Vehicles/
│       ├── CreateVehicle.cs
│       ├── CreateVehicleHandler.cs
│ ├── Application.csproj
│ ├── Class1.cs
│
│
├── Domain/
│ ├── Entities/
│       ├──Auth/
│           ├── RefreshToken.cs
│           ├── Rol.cs
│           ├── UserMember.cs
│           ├── UserMemberRol.cs
│       ├──Enums/
│           ├── OrderStatus.cs
│           ├── PaymentMethod.cs
│           ├── ServiceType.cs
│       ├── Customer.cs
│       ├── Invoice.cs
│       ├── OrderDetail.cs
│       ├── ServiceOrder.cs
│       ├── SparePart.cs
│       ├── Vehicle.cs
│ ├── Class1.cs
│ ├── Domain.csproj
│
│
├── Frontend/
│ ├── css/
│       ├── admin.css
│       ├── login.css
│       ├── recepcionista.css
│       ├── SignUp.css
│ ├── js/
│       ├── clientes.js
│       ├── Config.js
│       ├── dashboard.js
│       ├── empleados.js
│       ├── login.js
│       ├── mecanico.js
│       ├── recepcionista.js
│       ├── repuestos.js
│       ├── signUp.js
│       ├── vehiculos.js
│ ├── SignUp.html
│ ├── admin.html
│ ├── index.html
│ ├── mechanic.html
│ ├── receptionist.html
│
│
├── Infrastructure/
│ ├── Migrations/
│       ├── 2025101023318_IniMig.Designer.cs
│       ├── 20251010233118_IniMig.cs
│       ├── AutoTallerDbContextModelSnapshot.cs
│ ├── Persistence/
│       ├── Configurations/
│         ├──Auth/
│           ├── RefreshTokenConfiguration.cs
│           ├── RolConfiguration.cs
│           ├── UserMemberConfiguration.cs
│           ├── UserMemberRolConfiguration.cs
│         ├── CustomerConfiguration.cs
│         ├── InvoiceConfiguration.cs
│         ├── OrderDetailConfiguration.cs
│         ├── ServiceOrderConfiguration.cs
│         ├── SparePartConfiguration.cs
│         ├── VehicleConfiguration.cs
│       ├── Repositories/
│         ├──Auth/
│           ├── RefreshTokenService.cs
│           ├── RolService.cs
│           ├── UserMemberRolService.cs
│           ├── UserMemberService.cs
│         ├── CustomerRepository.cs
│         ├── InvoiceRepository.cs
│         ├── ServiceOrderRepository.cs
│         ├── SparePartRepository.cs
│         ├── VehicleRepository.cs
│       ├── AutoTallerDbContext.cs
│ ├── UnitOfWork/
│       ├── UnitOfWork.cs
│ ├──Class1.cs
│ ├── Infrastructure.csproj
│
│
├── docker/
│ ├── docker-compose.yml
│
├── .gitignore
├── AutoTallerManager.sln
└── README.md
```
### Configuración con Fluent API
El archivo `AutoTallerDbContext.cs` contiene:
- Configuración de entidades con Fluent API
- Definición de claves primarias y foráneas
- Restricciones de integridad y longitudes
- Índices únicos (VIN, código de repuesto)
- Comportamientos de borrado en cascada

## Clases por Componente

### Componente Cliente
- **Cliente**: Entidad principal del propietario
- **ClienteDto**: DTO para transferencia de datos
- **ClienteService**: Servicio de lógica de negocio
- **ClientesController**: API REST para gestión de clientes

### Componente Vehículo
- **Vehiculo**: Entidad de vehículo automotor
- **VehiculoDto**: DTO para transferencia de datos
- **VehiculoService**: Servicio de lógica de negocio
- **VehiculosController**: API REST para gestión de vehículos

### Componente Orden de Servicio
- **OrdenServicio**: Entidad de solicitud de trabajo
- **DetalleOrden**: Entidad de detalle de repuestos
- **OrdenServicioDto**: DTO para transferencia de datos
- **OrdenServicioService**: Servicio de lógica de negocio
- **OrdenesServicioController**: API REST para gestión de órdenes

### Componente Repuesto
- **Repuesto**: Entidad de pieza o insumo
- **RepuestoDto**: DTO para transferencia de datos
- **RepuestoService**: Servicio de lógica de negocio
- **RepuestosController**: API REST para gestión de inventario

### Componente Facturación
- **Factura**: Entidad de documento de cobro
- **FacturaDto**: DTO para transferencia de datos
- **FacturaService**: Servicio de lógica de negocio
- **FacturasController**: API REST para generación de facturas

### Componente Usuario
- **Usuario**: Entidad de personal del taller
- **UsuarioDto**: DTO para transferencia de datos
- **UsuarioService**: Servicio de autenticación
- **UsuariosController**: API REST para gestión de usuarios

### Componente Shared
- **AutoTallerDbContext**: Contexto de Entity Framework Core
- **GenericRepository<T>**: Repositorio genérico con CRUD
- **UnitOfWork**: Patrón Unit of Work para transacciones
- **JwtTokenService**: Servicio de generación de tokens JWT

## Funcionalidades Implementadas

### ✅ Completadas
- **Gestión de Clientes**: CRUD completo con validaciones
- **Gestión de Vehículos**: Registro con VIN único y asociación a clientes
- **Órdenes de Servicio**: Creación, actualización, cancelación y cierre
- **Gestión de Repuestos**: Control de inventario con stock
- **Facturación Automática**: Generación al cerrar órdenes
- **Autenticación JWT**: Login seguro con tokens
- **Autorización por Roles**: Admin, Mecánico, Recepcionista
- **Rate Limiting**: Control de solicitudes por endpoint
- **Paginación**: Listados eficientes con Skip/Take
- **Validaciones de Negocio**: Reglas de inventario y disponibilidad
- **Transacciones Atómicas**: Unit of Work para consistencia
- **Documentación Swagger**: API interactiva y autodocumentada

### 🔧 Características Técnicas
- **ASP.NET Core 8.0**: Framework moderno y de alto rendimiento
- **Entity Framework Core**: ORM con Fluent API
- **MySQL**: Base de datos relacional robusta
- **AutoMapper**: Mapeo automático entre entidades y DTOs
- **JWT Authentication**: Seguridad basada en tokens
- **AspNetCoreRateLimit**: Control de tráfico por endpoint
- **Swagger/OpenAPI**: Documentación interactiva
- **Async/Await**: Programación asíncrona para escalabilidad
- **LINQ**: Consultas eficientes y expresivas
- **Dependency Injection**: Arquitectura desacoplada y testeable

## Instalación y Configuración

### Prerrequisitos
- .NET 8.0 SDK o superior
- Visual Studio 2022, Rider o VS Code
- Postman o herramienta similar (opcional)

### Instalación Dotnet ef
```
dotnet tool install --global dotnet-ef --version 9.0.9
```

### Comando para migracion
```
dotnet ef database update -p Infrastructure/ -s Api/
```
## Roles y Permisos

### Admin
- ✅ Acceso total a todos los recursos
- ✅ Gestión de usuarios y roles
- ✅ Configuración del sistema
- ✅ Alta/baja de repuestos
- ✅ Reportes y estadísticas

### Mecánico
- ✅ Actualizar estado de órdenes
- ✅ Registrar trabajo realizado
- ✅ Generar facturas
- ✅ Consultar repuestos

### Recepcionista
- ✅ Crear órdenes de servicio
- ✅ Consultar clientes y vehículos
- ✅ Ver estado de órdenes

## Validaciones Implementadas

### Cliente
- Nombre requerido (máx. 100 caracteres)
- Teléfono con formato válido
- Correo electrónico único y válido

### Vehículo
- VIN único (17 caracteres)
- Marca y modelo requeridos
- Año entre 1900 y año actual + 1
- Kilometraje no negativo
- Cliente asociado debe existir

### Orden de Servicio
- Vehículo debe existir
- No puede haber dos órdenes activas para el mismo vehículo
- Tipo de servicio válido (Mantenimiento, Reparación, Diagnóstico)
- Fecha estimada posterior a fecha de ingreso
- Mecánico asignado debe existir

### Repuesto
- Código único (máx. 50 caracteres)
- Descripción requerida (máx. 200 caracteres)
- Stock no negativo
- Precio unitario mayor a cero

### Factura
- Orden de servicio debe existir y estar cerrada
- Cálculo automático de subtotal, IVA y total
- Método de pago válido (Efectivo, Tarjeta, Transferencia)

## Manejo de Errores

### Estrategias Implementadas
- **Global Exception Middleware**: Captura todas las excepciones no controladas
- **Try-Catch**: En servicios críticos con logging detallado
- **Validaciones de Negocio**: Previas a operaciones de base de datos
- **Códigos HTTP Apropiados**: 200, 201, 204, 400, 404, 409, 500
- **Mensajes Descriptivos**: Respuestas JSON con detalles del error

## Autores
- **Fabio Hernández** - [fabioo-hm](https://github.com/fabioo-hm)
- **David Castillo** -  [davidsc21](https://github.com/davidsc21)
- **Sebastian Mora** -  [sebastian221-art](https://github.com/sebastian221-art)
- **Dylan** - [Dylan3-cpu](https://github.com/Dylan3-cpu)