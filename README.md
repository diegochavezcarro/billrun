# Ejemplo de Spring Cloud Task y Spring Cloud Data Flow:

### Basado en:

* https://dataflow.spring.io/docs/batch-developer-guides/batch/spring-batch/

(Opcional) Si se quiere otro ejemplo de Spring Batch ver:

https://github.com/diegochavezcarro/gs-batch-processing-complete

### Pasos:

* Si se quiere usar mysql setearlo:

docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=task -d mysql:5.7.25

* Primero probar la aplicación con h2. El Test se deberia ejecutar bien.

Si se quieren ver las tablas generadas en H2 tanto por el ejemplo como por Spring Batch 
(de hecho esto es una app de ese tipo, que al agregarsele la libreria de 
Spring Cloud Task y la annotation @EnableTask pasa a ser tambien
una app de Spring Cloud Task) como por Spring Cloud Task y la 
relacion entre ellas descomentar en el pom.xml la parte Web y ver las tablas en:

http://localhost:8080/h2-console

* Si se quiere probar el ejemplo con mysql descomentar las propiedades del
application.properties y probar luego si se creó la tabla y su contenido: 

$ docker exec -it mysql bash -l

# mysql -u root -ppassword

mysql> select * from task.BILL_STATEMENTS

Si en este caso también se quiere integrar con el ejemplo:

https://github.com/diegochavezcarro/billsetuptask

Ejecutandolo primero a ese y luego a este se puede cambiar la propiedad 
spring.batch.initialize-schema 
para no sobrescribir la creacion de la base y tabla ya creada por ese ejemplo.
En el caso de H2 esto no se puede ya que cada ejemplo crea su propia base en memoria.

### Spring Cloud Data Flow

* Ver:

https://github.com/diegochavezcarro/billsetuptask
