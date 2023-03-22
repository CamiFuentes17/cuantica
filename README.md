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
   ![image](https://user-images.githubusercontent.com/26396833/226799704-92b69af0-5f4d-43d5-b97c-8a3460611505.png)

## Conclusión

Por ultimo cabe mencionar que como pudimos demostrar en  este proceso, qiskit es un conjunto de algoritmos de optimización cuántica generados de manera fácil de usar, disponibles y listo, el código está abierto para que puedas usarlo vía Qiskit. 
 
Solo para aclarar que la sección de optimización contiene múltiples proyectos para realizar el ejercicio que estamos haciendo en este caso (optimización con Qiskit), cómo funciona Vehicle Routing en este caso Ejecute un proceso para verificar si vincula 
 
El propósito de este método es lo que sea que haga Esto se hace en base a un algoritmo híbrido alternativo de computadora cuántica con resultados adicionales. se visualiza. 
 
Qiskit realiza esto comparando y mejorando a través de modelos matemáticos y cuánticos. 
 

