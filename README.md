# scheduling
comprendiendo schedulin con spring boot

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
<b> 1 Tarea programada con intervalos fijos (Fixed Rate)</b><br>
  Puedes programar un metodo para que se ejecute en un intervalo fijo usando el parametro fixedRate en la notacion @Scheduled<br>
  En el ejemplo el metodo anotado se ejecutara cada 2 segundos<br>
@Scheduled(fixedRate = 2000)
public void scheduleTaskWithFixedRate() {<br>
    $nbsp;&nbsp;logger.info("Fixed Rate Task :: Execution Time - {}", dateTimeFormatter.format(LocalDateTime.now()) );<br>
}<br>
  ojo, FixedRate se invoca en el intervalo especificado, incluso, si la invocacion anterior no ha terminado.<br>
Output<br>
Fixed Rate Task :: Execution Time - 10:26:58<br>
Fixed Rate Task :: Execution Time - 10:27:00<br>
Fixed Rate Task :: Execution Time - 10:27:02<br>
....<br><br>
  
<b> 2 Tarea programada con retraso Fijo (Fixed Delay)</b><br>
  Puedes ejecutar una tarea con un retraso Fijo entre la finalizacion de la ultima invocacion y el inicio de la siguiente, usando el parametro fixedDelay. Ese retraso es el fixedDelay.<br>
@Scheduled(fixedDelay = 2000)
public void scheduleTaskWithFixedDelay() {<br>
    &nbsp;logger.info("Fixed Delay Task :: Execution Time - {}", dateTimeFormatter.format(LocalDateTime.now()));<br>
    &nbsp;&nbsp;try {<br>
    &nbsp;&nbsp;&nbsp;TimeUnit.SECONDS.sleep(5);<br>
    &nbsp;&nbsp;} catch (InterruptedException ex) {<br>
    &nbsp;logger.error("Ran into an error {}", ex);<br>
    &nbsp;throw new IllegalStateException(ex);<br>
    }<br>
}<br>
  ojo, Como la tarea en sí tarda 5 segundos en completarse y hemos especificado un retraso de 2 segundos entre la finalización de la última invocación y el inicio de la siguiente, habrá un retraso de 7 segundos entre cada invocación:<br>
  Output<br>
Fixed Delay Task :: Execution Time - 10:30:01<br>
Fixed Delay Task :: Execution Time - 10:30:08<br>
Fixed Delay Task :: Execution Time - 10:30:15<br>
....<br><br>

  
