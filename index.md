
\clearpage

# PAQUETES DE R

## Bookmarkr:

Extraño paquete de Jonathan de RStudio (jmcphers - <https://github.com/jmcphers/bookmarkr>); extraño aunque simple. No deja de ser el añadir un Addin a RStudio por el que puedes marcar una línea de código con un bookmark y un pequeño comentario. Luego puedes ir a la pestaña de "Markers" y revisitarlos. Lo encuentro útil para scripts que requieren revisiones largas y es conveniente no olvidarse de ciertos detalles a resolver sin por ello tener que llenar el script de comentarios. Enjoy.

```{r echo=TRUE, eval=FALSE}
# https://github.com/jmcphers/bookmarkr

install.packages("devtools")
library(devtools)
devtools::install_github("jmcphers/bookmarkr")
library(bookmarkr)
```

# OBJETIVOS Y USOS EN R

## Obtener Datos del PC y Sesión:

Esta es una task que se puede hacer con R a veces de forma más fácil y rápida que visualmente buscando en el panel de control del PC. Al ser una tarea, más que una descripción de un paquete, en realidad se pueden utilizar muchos packs. y muchas funciones. Según vaya encontrando más, podré ir añadiendo; de momento las que me parecen útiles son las que aparecen a continuación. Con ellas se puede obtener: datos de la CPU (e.g., **"Intel(R) Core(TM) i7-7700 CPU \@ 3.60GHz"**), Nº de núcleos, Nº de núcleos reales, la RAM, información de la sesión de trabajo, versión de R, y otros detalles del sistema en cuestión sobre el que se está trabajando.

```{r echo=TRUE, eval=FALSE}

install.packages(c("doParallel","benchmarkme"))
library(doParallel); library(benchmarkme)

  ## Return the machine CPU
  cat("Machine:     "); print(get_cpu()$model_name)
  
  ## Return number of true cores
  cat("Num cores:   "); print(detectCores(logical = FALSE))
  
  ## Return number of threads
  cat("Num threads: "); print(detectCores(logical = TRUE))
  
  ## Return the machine RAM
  cat("RAM:         "); print(get_ram()); cat("\n")

  ## Return platform info
  get_platform_info()
  
  ## Return R version
  get_r_version()
  
  ## Return System Details
  get_sys_details()
  
```

## Obtener una muestra aleatoria de filas de un data.frame

```{r}
df = data.frame(matrix(rnorm(20), nrow=20))
df[sample(nrow(df), 15), ]
```

# FUNCIONES DE GRAN UTILIDAD

## memory.size()

Esta función es útil para trabajar en windows y asignar memoria a R. Con el código aquí incorporado lo que se hace es incrementar los límites de memoria asignados a R hasta el máximo. Es útil para optimizar algún código que roza la capacidad máxima del PC.

```{r echo=TRUE, eval=FALSE}

memory.size(max = TRUE)

```
