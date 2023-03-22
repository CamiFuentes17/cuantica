# Introducción a computación cuántica 

> Se ha realizado la ejecución de un problema en computación cuántica basado en Grover Optimizer 
 
## Requisitos para realizar el proceso 

Tener instalado 
Jypiter, Anaconda, Python, Librerias de qiskit 
| Instalación      | Ejecución                               | Resultados                            |
|------------------|------------------------------------------ |-------------------------------------    |
| 1️⃣ Jypiter      | 1️⃣ Realizamos bajo el siguiente comando ```python pip install jupyterlab ```| 1️⃣ se había ejecutado el proceso por lo cual ya cuenta con la instalación ![image](https://user-images.githubusercontent.com/26396833/226795395-929b530c-f1fe-41b2-a795-582a0b7bdb1a.png)| 
| 2️⃣ Anaconda     | 2️⃣ Realizamos la instalación desde:https://www.anaconda.com/ ![image](https://user-images.githubusercontent.com/26396833/226793200-19b2d1e5-0f77-4bf1-a66f-98658701e462.png) | 2️⃣ Ingresamos al navegador y así poder probar funcionalidad| 
| 3️⃣ Python       | 3️⃣ Instalamos desde la página oficial la última versión: https://www.python.org/downloads/ ![image](https://user-images.githubusercontent.com/26396833/226794561-3823d1e2-9c96-40c2-821a-d98041e94f14.png)| 3️⃣ Buscamos nuestro instalador![image](https://user-images.githubusercontent.com/26396833/226794666-7ec3062b-214d-499f-88b8-64e166b7471f.png)|
| 4️⃣ Qiskit       | 4️⃣ Realizamos la instalación bajo los siguientes comandos **1.** ```pip install qiskit``` **2.** ```pip install qiskit[visualization]```| 4️⃣ Resultados de la instalación | 

> Para empezar vamos a lanzar jupyter lab
> ![image](https://user-images.githubusercontent.com/26396833/226796204-04d8af2b-82a2-4a1d-ade5-51f83a7ecb9d.png)
> Queremos abrir el archivo que alojamos en el escritorio
> ![image](https://user-images.githubusercontent.com/26396833/226796326-4889b421-5b42-47d6-afb7-9fbe3a06f375.png)
> Empezamos a lanzar el código 
> ![image](https://user-images.githubusercontent.com/26396833/226796410-155bbf79-edba-4a38-a9f5-cfc139d155c7.png)


Una vez que estés lista, sigue las instrucciones de la documentación que revisaremos a continuación.

### Pasos
1. Ejecutar el comando de código 
   ```from qiskit.algorithms.minimum_eigensolvers import NumPyMinimumEigensolver
      from qiskit.primitives import Sampler
      from qiskit_optimization.algorithms import GroverOptimizer, MinimumEigenOptimizer
      from qiskit_optimization.translators import from_docplex_mp
      from docplex.mp.model import Model
   ```
   ![image](https://user-images.githubusercontent.com/26396833/226799046-4f572097-9566-4fb3-8391-9c50b6429e55.png)

El código que se muestra importa diferentes módulos y clases necesarias para resolver problemas de optimización cuántica utilizando Qiskit.

En primer lugar, se importa la clase NumPyMinimumEigensolver del módulo qiskit.algorithms.minimum_eigensolvers. Esta clase proporciona un solucionador mínimo de autovalores utilizando el paquete NumPy. Esta clase se utiliza para resolver el problema de autovalores mínimo que se encuentra al resolver el problema de optimización cuántica.

A continuación, se importa la clase Sampler del módulo qiskit.primitives. Esta clase se utiliza para generar muestras de un circuito cuántico. En el contexto de la optimización cuántica, esto se utiliza para estimar la función de costo de un problema de optimización cuántica.

Luego, se importa la clase GroverOptimizer del módulo qiskit_optimization.algorithms. Esta clase implementa el algoritmo de Grover para resolver problemas de optimización cuántica. El algoritmo de Grover es un algoritmo de búsqueda cuántica que se utiliza para encontrar la solución óptima de un problema de optimización cuántica.

A continuación, se importa la clase MinimumEigenOptimizer del módulo qiskit_optimization.algorithms. Esta clase utiliza un solucionador de autovalores mínimo para resolver problemas de optimización cuántica.

Luego, se importa la función from_docplex_mp del módulo qiskit_optimization.translators. Esta función se utiliza para convertir modelos de optimización lineal y entera de CPLEX de IBM en un objeto QuadraticProgram de Qiskit que puede ser utilizado para resolver problemas de optimización cuántica.

Finalmente, se importa la clase Model del módulo docplex.mp.model. Esta clase se utiliza para definir modelos de optimización lineal y entera utilizando la sintaxis de la librería CPLEX de IBM.

2. Esperamos que no genere errores para continuar , enviamos la otra parte y el resultado debe ser el mismo que en el documento
   ```
   model = Model()
   x0 = model.binary_var(name="x0")
   x1 = model.binary_var(name="x1")
   x2 = model.binary_var(name="x2")
   model.minimize(-x0 + 2 * x1 - 3 * x2 - 2 * x0 * x2 - 1 * x1 * x2)
   qp = from_docplex_mp(model)
   print(qp.prettyprint())
   ```
   ![image](https://user-images.githubusercontent.com/26396833/226799262-b58dea95-3124-4f91-a010-8bf57a797765.png)

3. Realizamos la ejección de la otra sección 
   ```
   grover_optimizer = GroverOptimizer(6, num_iterations=10, sampler=Sampler())
   results = grover_optimizer.solve(qp)
   print(results.prettyprint())
   ```
   
   comienza creando una instancia de la clase GroverOptimizer. GroverOptimizer es un algoritmo de búsqueda cuántica que utiliza el algoritmo de Grover para buscar en una lista no ordenada de elementos y encontrar la solución óptima. En este caso, se especifica que se utilizarán 6 qubits y que se realizarán 10 iteraciones del algoritmo de Grover.

Luego, la instancia de GroverOptimizer llama al método "solve" y pasa el objeto de problema cuántico "qp" como argumento. Este objeto se crea utilizando la función "from_docplex_mp" que se importó anteriormente. Esta función toma una instancia de un modelo de Docplex y lo convierte en un problema cuántico, que es lo que se necesita para resolver problemas de optimización cuántica.

Por último, los resultados del problema cuántico se imprimen utilizando el método "prettyprint". Esto mostrará la solución óptima encontrada para el problema cuántico en un formato legible para el usuario.

   ![image](https://user-images.githubusercontent.com/26396833/226799522-604d6683-f2f8-4c38-acab-d3e0b3c06680.png)


4. Continuamos con el proceso
   ```
   exact_solver = MinimumEigenOptimizer(NumPyMinimumEigensolver())
   exact_result = exact_solver.solve(qp)
   print(exact_result.prettyprint())
   ```
   ![image](https://user-images.githubusercontent.com/26396833/226799609-a55a8371-e490-499a-b984-e4aa33f90390.png)

5. Como resultado tenemos
   ```
   import qiskit.tools.jupyter
   %qiskit_version_table
   %qiskit_copyright
   ```
   Estos comandos son utilizados en el entorno de Jupyter Notebook para obtener información sobre la versión de Qiskit instalada y mostrar el aviso de derechos de autor de Qiskit.

El comando %qiskit_version_table muestra una tabla con información detallada sobre la versión actual de los paquetes de Qiskit instalados, incluyendo el nombre del paquete, la versión, la ubicación del archivo, la versión de Python compatible y la fecha de lanzamiento.

El comando %qiskit_copyright muestra el aviso de derechos de autor de Qiskit. Este comando es útil para saber los términos y condiciones de uso de la biblioteca de Qiskit y sus paquetes.
   
   ![image](https://user-images.githubusercontent.com/26396833/226799704-92b69af0-5f4d-43d5-b97c-8a3460611505.png)

## Conclusión

Por ultimo cabe mencionar que como pudimos demostrar en  este proceso, qiskit es un conjunto de algoritmos de optimización cuántica generados de manera fácil de usar, disponibles y listo, el código está abierto para que puedas usarlo vía Qiskit. 
 
Solo para aclarar que la sección de optimización contiene múltiples proyectos para realizar el ejercicio que estamos haciendo en este caso (optimización con Qiskit), cómo funciona Vehicle Routing en este caso Ejecute un proceso para verificar si vincula 
 
 Esto se hace en base a un algoritmo híbrido alternativo de computadora cuántica con resultados adicionales. se visualiza. 
 
Qiskit realiza esto comparando y mejorando a través de modelos matemáticos y cuánticos. 
 

