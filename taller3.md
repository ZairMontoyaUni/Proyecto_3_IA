Ingeniería de Sistemas y Computación
ISIS-1611: Inteligencia artificial
Semestre: 2026-10
Créditos: 3
Taller 3: Investigación Criminalística con Lógica
En este taller su equipo se convertirá en detectives. Su misión: resolver cinco casos criminales usando
herramientas de lógica formal. Aplicarás lógica proposicional (model checking, forma normal
conjuntiva, resolución) y lógica de predicados (cláusulas de Horn, encadenamiento hacia adelante y
hacia atrás) para determinar quién es culpable, quién está descartado y quién encubre al criminal.
El proyecto incluye un motor de lógica completo. Su trabajo consiste en implementar funciones clave
del motor proposicional e implementar las bases de conocimiento de los casos criminales usando
lógica de predicados.
Objetivos de aprendizaje
• Implementar funciones de model checking para lógica proposicional.
• Implementar las transformaciones necesarias para convertir fórmulas a Forma Normal
Conjuntiva (CNF).
• Modelar casos criminales con lógica de predicados usando cláusulas de Horn.
• Comparar y reflexionar sobre los diferentes métodos de inferencia lógica.
Recursos de Apoyo
El proyecto incluye varios recursos para ayudar a entender el motor de lógica. Estos recursos no son
evaluados. La calificación se basa exclusivamente en las pruebas unitarias y las preguntas de análisis.
• Guía de Objetos en Python: notebooks/guia_objetos_python.ipynb
• Guía interactiva sobre Model Checking: notebooks/parte1_model_checking.ipynb
• Guía interactiva sobre transformación a CNF: notebooks/parte2_cnf.ipynb
• Guía interactiva sobre lógica de predicados: notebooks/parte3_predicados.ipynb
• Interfaz de terminal para explorar los casos de forma interactiva: uv run main.py
• Estructura del repositorio e instrucciones de inicio rápido: README.md
Punto 1: Model Checking (20%)
Implementen las 5 funciones en src/model_checking.py. Cada función tiene un docstring con
su descripción, ejemplo de uso y hints para la implementación.
Funciones a implementar
• get_all_models(atoms): Genera todos los modelos posibles (asignaciones de verdad)
para un conjunto de átomos. Para n átomos, debe generar 2! modelos.



|  | Ingeniería de Sistemas y Computación
ISIS-1611: Inteligencia artificial
Semestre: 2026-10
Créditos: 3 |  |
| --- | --- | --- |




---


• check_satisfiable(formula): Determina si una fórmula es satisfacible. Retorna (True,
modelo) si encuentra un modelo que satisface la fórmula, o (False, None) si es insatisfacible.
• check_valid(formula): Determina si una fórmula es una tautología (válida en todo
modelo posible).
• check_entailment(kb, query): Determina si KB |= query, es decir, si la base de
conocimiento implica la consulta.
• truth_table(formula): Genera la tabla de verdad completa de una fórmula.
Punto 2: Conversión a CNF (40%)
Implementen las 5 funciones de transformación en src/cnf_transform.py. La función
eliminate_double_negation y el pipeline completo to_cnf ya están dados como referencia.
Funciones a implementar
• eliminate_iff(formula): Elimina bicondicionales 𝐴↔𝐵
• eliminate_implication(formula): Elimina implicaciones 𝐴→𝐵
• push_negation_inward(formula): Aplica las leyes de De Morgan.
• distribute_or_over_and(formula): Distribuye Or sobre And.
• flatten(formula): Aplana conjunciones y disyunciones anidadas.
Punto 3: Lógica de Predicados (30%)
En esta sección modelarán cinco casos criminales usando lógica de predicados con cláusulas de Horn.
Los motores de forward chaining y backward chaining ya están implementados. Su trabajo es definir
correctamente los hechos y reglas de cada caso.
3a. Implementación de casos criminales (15%)
Cada archivo en crimes/ contiene un docstring con la narrativa del caso en dos párrafos: el primero
describe los hechos y el segundo describe las reglas de deducción. Implementen la función
crear_kb() en cada archivo.
Archivos a implementar:
• crimes/veneno_villa_espinas.py
• crimes/robo_expreso_sur.py
• crimes/sabotaje_pharmax.py
• crimes/herencia_hacienda_rosal.py
• crimes/red_puerto_sombras.py
3b. Preguntas de análisis cualitativo (15%)
Responde las siguientes preguntas a partir del modelado de casos criminales en lógica de predicados
y su experimentación con los motores de lógica proporcionados:
• ¿Cómo se modela la diferencia entre evidencia directa (por ejemplo, huellas en el arma) e
indirecta (por ejemplo, un testimonio) usando predicados y reglas?


---


• ¿Qué sucede si un sospechoso tiene tanto evidencia en su contra como coartada verificada?
¿El motor detecta esta contradicción? Explica con un ejemplo.
• ¿En qué se diferencia razonar con forward chaining vs. backward chaining al resolver un
caso? ¿Cuándo conviene usar cada uno?
• ¿Qué rol juegan las variables vs. las constantes en la expresividad de las reglas? ¿Qué se
perdería si solo se usaran constantes?
• ¿Cómo afecta la suposición de mundo cerrado (lo que no se puede probar es falso) a las
conclusiones sobre sospechosos que no tienen evidencia en su contra ni coartada verificada?
Punto 4: Reflexión (10%)
Escriba una reflexión que aborde los siguientes puntos:
• (5%) Para cada uno de los puntos anteriores, explique brevemente: ¿Qué enfoque utilizó para
su implementación? ¿Qué dificultades encontró? ¿Cómo verificó que su implementación era
correcta?
• (5%) Escriba una reflexión concisa sobre la co-construcción de la solución con apoyo de la IA
(vea política de uso más adelante), indicando qué aprendizajes obtuvo, si las correcciones de la
IA fueron básicas o mejoras secundarias, y los beneficios y limitaciones de la IA en este contexto.
Bono: Caso Criminal Original (+10%)
Creen su propio caso criminal original como un nuevo archivo en crimes/. Su caso debe seguir la
misma estructura que los casos existentes.
Requisitos mínimos
• Al menos 4 sospechosos (mínimo uno debe ser culpable)
• Al menos 6 hechos (add_fact)
• Al menos 4 reglas (add_rule)
• Al menos 5 consultas verificadas con backward chaining
• Al menos una consulta que use ExistsGoal o ForallGoal
• Un docstring con la narrativa en dos párrafos (hechos y reglas)
• Todas las consultas deben resolverse correctamente
Evaluación
Este taller incluye un conjunto de pruebas unitarias en tests/ que pueden ser utilizadas para validar
su implementación. Pueden ser ejecutadas con el comando: uv run main.py -–test. Se debe
tener en cuenta que la evaluación final se realizará con un conjunto distinto de pruebas, por lo cual
el desempeño en las pruebas suministradas no puede considerarse equivalente a la nota obtenida en
el taller. Se recomienda que utilicen dichas pruebas para encontrar errores durante el desarrollo, e
incluso que añadan pruebas propias para asegurarse de que sus algoritmos manejan casos de
frontera de forma adecuada.


---


Política de Uso de IA Generativa y presentación en el trabajo a entregar
Para este taller se espera que usted desarrolle una primera versión de la solución de forma
completamente autónoma, usando su propio criterio, conocimiento y creatividad antes de recurrir a
herramientas de IA. La IA puede emplearse después para mejoras puntuales, refactorización,
comentarios de calidad o apoyo en la corrección de errores, pero nunca como sustituto del esfuerzo
personal ni como generador principal del código. Use estas herramientas con criterio profesional,
asumiendo responsabilidad sobre su proceso de aprendizaje y entendiendo que lo que más valor
tiene aquí es el camino que usted recorre para llegar a la solución, no solo el resultado final.
Todos los prompts y las versiones de código generadas con apoyo de IA deben quedar registrados
dentro de los archivos del proyecto. Si utiliza IA para refactorizar u optimizar su solución, incluya en
el archivo: (1) la versión inicial del código, (2) los prompts que utilizó para refinarla y (3) la versión
final del código. Al finalizar, deje como código activo únicamente la versión final y conserve la versión
inicial y todos los prompts en forma de comentarios dentro del mismo archivo.
Entrega del trabajo
• Guarde todo su trabajo (incluyendo el documento PDF) en una carpeta comprimida (.zip).
• Suba el trabajo al espacio correspondiente en Bloque Neón a más tardar la fecha y hora
indicadas (un solo miembro del grupo debe subir el trabajo).
• Recuerde incluir los nombres y códigos de todos los integrantes de su grupo.
Nota: Al enviar su solución, usted declara que el código entregado en la primera versión de cada
punto es de su autoría y que las versiones que utilizan IA fueron la respuesta a los prompts incluidos,
que comprende el funcionamiento en todas las versiones y que acepta que este material pueda ser
revisado, ejecutado y evaluado por el equipo docente para efectos académicos y de verificación de
originalidad.