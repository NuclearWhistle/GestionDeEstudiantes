principales funcionalidades del programa y cómo interactúan las estructuras de datos mencionadas:

1. Agregar Estudiante:  
   El programa permite agregar un nuevo estudiante a través de la entrada de los datos: ID, nombre, curso, promedio y edad. Estos valores se almacenan en un objeto de tipo Estudiante, que luego es agregado al vector estudiantes.

2. Mostrar Estudiantes:  
   El programa permite mostrar todos los estudiantes registrados. Para esto, recorre el vector y presenta los datos de cada estudiante en formato tabular. Se utiliza setw para alinear las columnas y mejorar la legibilidad de la información.

3. Editar Estudiante:  
   Si se desea modificar los datos de un estudiante, el programa solicita el ID del estudiante a editar. Luego, busca el estudiante en el vector y permite modificar sus datos, como el nombre, curso, promedio y edad.

4. Mostrar Promedio de Notas:  
   Esta opción permite calcular el promedio de las calificaciones de todos los estudiantes registrados. El programa recorre el vector, suma los promedios individuales y divide entre la cantidad de estudiantes para obtener el promedio general.

5. Guardar Datos:  
   El programa tiene la opción de guardar los datos de los estudiantes en un archivo de texto. Cada estudiante se guarda en una línea separada, con sus atributos separados por comas. Este archivo puede ser utilizado para mantener los datos entre diferentes ejecuciones del programa.

6. Cargar Datos:  
   Al inicio del programa, se cargan los datos previamente guardados desde el archivo. El programa lee cada línea del archivo y utiliza stringstream para procesar y extraer los datos, que luego se almacenan en el vector estudiantes. Este proceso garantiza que los datos se mantengan entre sesiones del programa.

