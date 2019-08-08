# scheduling
understanding schedulin in spring boot

Crea un proyecto usando http://start.spring.io/
Artifactory = “scheduler-demo”
No tienes que descargar ningun jar
Generas el proyecto
<br><br>

<b>Habilitas el Scheduling</b><br>
@SpringBootApplication<br>
@EnableScheduling<br>
public class SchedulerDemoApplication<br>
<br><br>
<b> Programando tares con Scheduling</b>
Scheduling con Spring boot es tan simple como ponerle la anotacion @Scheduled al metodo ponerle algunos parametros que usara para decirle el momento que debe ejecutarse la tarea.
<br>
Agregaremos una nueva clase ScheduledTasks anotado con @Component para que sea reconocido como bean, aqui probaremos las tareas programadas, que son 4.<br>
Los metodos que van implementar el schedule deben cumplir con 2 criterios<br>
-El metodo debe tener el tipo de retorno void<br>
-El metodo no debe tener argumentos<br>
Pasemos ahora a la implementacion
<br><br>
<b> 1 Tarea programada con intervalos fijos (Fixed Rate)<b>

  
