# Apunte Spring

### Estructura de archivos

    /Controllers: Punto inicial de la aplicacion, recibe la peticion y ejecuta la logica principal

        UserController.java

    /Services: Lo que el usuario puede realizar en mi sistema, las acciones permitidas (Actualizar, obtener informacion, modificar datos)

        UserService.java

    /Repositories: Consultas SQL o metodos de mapeo de objetos (interfaz). Extendemos de la clase CrudRepository <UserModel, Long>

        UserRepository.java

    /Models: Mapear una tabla de la BD a una clase de java, clase que posee los atributos que posee nuestro elemento de la BD (id, nombre, email)

        UserModel.java

    Controller usa servicio, servicio usa repositorio, repositorio usa modelo

### Notaciones/Etiquetas


    Spring:

    @RestController: indica a spring que la clase es un controlador.

    @RequestMapping("/"): indica que se ejecuta ese metodo cuando visitamos la raiz.

    @AutoWired: Notifica a Spring que ya existe una instancia, y sabe cual va a utilizar

    @GetMapping: indicar que cuando llega una peticion de tipo get del navegador o de un cliente, ejecuta este metodo

    @PostMaping: Abreviacion para RequestMapping(method = RequestMethod.POST)

    @RequestBody: Todos los clientes pueden enviar info dentro del cuerpo de la solicitud http

    javax.persistence.*:

        @Table(name = "user"): Se coloca sobre la clase del modelo, aqui garantizamos controlar siempre el nombre de nuestra tabla

        @Entity: Se coloca sobre la clase modelo con @Table, esto nos indica que es un modelo real

        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        @Column(unique = true, nullable = false) : 
        Esto se coloca sobre un atributo, en este caso seria sobre la id, y nos indica que es una id, que se genera automaticamente y se incremente, y que es unico y no puede ser nulo.

    @Repository: Se coloca sobre la interfaz del repositorio, indica que la interfaz es el repositorio

    @Service: Se coloca sobre la clase del servicio, indicando que es el servicio

    

     

### Comandos

    Ejecutar app mediante el plug - in de SpringBoot usando archivo maven, mostrara nuestro servidor TomCat en la terminal:

    Windows:
    mvnw.cmd spring-boot:run

    Mac/Linux:
    ./mvnw spring-boot:run


### application.properties

    En este archivo que se encuentra en /resources, se copian las propiedades que necesitamos para java para conectarnos con una BD:

    spring.datasource.url=jdbc:mysql://35.225.57.117:3306/springboot
    spring.datasource.username=root
    spring.datasource.password=springroot
    spring.jpa.hibernate.ddl-auto=update

    Viendolo por partes:

    1) url: cadena de conexion estandarizada
        35.225.57.117: Direccion ip
        3306: Puerto
        springboot: Nombre de la base de datos
    
    2) Usuario y contraseña: tal como se lee, un usuario y contraseña para conectarse

    3) ddl-auto: aqui si la base de datos ya existe ponemos none (Database First), si queremos crearla con nuestro codigo ponemos update (Code First), y la base se crea automaticamente, poniendo none queda manual.