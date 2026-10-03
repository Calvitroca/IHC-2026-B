# Writting 1

## Fundamentos de la teoría de sistemas y su relación con IHC

**Universidad de Guadalajara**  
**Centro Universitario de Ciencias Exactas e Ingenierías (CUCEI)**  
**Programa:** ICOM  
**Materia:** Interfaz Hombre-Computadora · IHC 2026 B  
**Estudiante:** Gonzalez Orozco Sergio Alonso  
**Código:** 217560905  
**Profesor:** José Antonio Aviña Méndez  
**Fecha:** 3 de octubre de 2026

<!-- pagebreak -->

## 1. Introducción

La teoría de sistemas permite estudiar un problema considerando sus componentes, sus relaciones y su interacción con el entorno. En ingeniería de software, esta perspectiva ayuda a entender que el comportamiento de una aplicación depende tanto de sus módulos como de la manera en que intercambian información.

En Interfaz Hombre-Computadora (IHC), el análisis también considera a la persona que utiliza el programa. Las acciones del usuario producen cambios en la aplicación; las respuestas visibles permiten interpretar esos cambios y decidir la siguiente acción. Por ello, una interfaz puede estudiarse como parte de un sistema de interacción.

Este reporte desarrolla los ocho conceptos del mapa conceptual elaborado para la actividad: teoría de sistemas, pensamiento sistémico, sistema, mapa de sistemas, clasificación, elementos, modelo y simulación. Después presenta un ejemplo matemático y un algoritmo ilustrativo para relacionarlos con la programación gráfica. El mapa es la evidencia original; el ejemplo se incorpora como complemento didáctico y no como una práctica de programación realizada.

## 2. Desarrollo conceptual

### 2.1. Teoría de sistemas y pensamiento sistémico (Q1 y Q2)

La teoría general de sistemas, asociada con Ludwig von Bertalanffy, propone estudiar conjuntos de elementos interrelacionados y buscar principios aplicables en distintas disciplinas. El análisis de las relaciones permite comprender comportamientos que no se explican estudiando cada parte por separado (Bertalanffy, 1968).

El pensamiento sistémico es una forma de abordar problemas mediante relaciones, patrones y ciclos de retroalimentación. En lugar de atribuir cada resultado a una causa aislada, considera cómo las acciones se influyen entre sí y cómo sus efectos pueden aparecer después de cierto tiempo. El mapa relaciona este enfoque con la visión holística, la causalidad circular y la interdependencia; Senge (1990) es una de sus referencias de base.

### 2.2. Sistema y mapa de sistemas (Q3 y Q4)

Un sistema es un conjunto de elementos que interactúan mediante relaciones. En sistemas diseñados por personas, como una aplicación, esas relaciones se organizan para cumplir un objetivo. Su comportamiento depende de las partes y de su organización; no basta con enumerar los componentes.

Un mapa de sistemas representa componentes, relaciones y flujos relevantes para un problema. Puede servir para analizar software, diseño de interfaces, negocios, salud pública, ecología, políticas públicas, educación o logística. El documento de esta actividad es un mapa conceptual de esos fundamentos; un mapa de una aplicación concreta mostraría sus actores, módulos y flujos específicos.

<!-- pagebreak -->

### 2.3. Clasificación de los sistemas (Q5)

El mapa organiza la clasificación mediante cinco criterios. Las categorías describen aspectos distintos, por lo que un mismo sistema puede pertenecer a varias a la vez.

| Criterio | Clasificación | Interpretación |
| --- | --- | --- |
| Relación con el entorno | Abiertos / cerrados | Se considera el intercambio con el entorno; el aislamiento depende de la frontera y de la disciplina de análisis. |
| Origen | Naturales / artificiales | Surgen de procesos naturales o son diseñados por personas. |
| Naturaleza | Concretos / abstractos | Se estudian como entidades materiales o representaciones conceptuales y simbólicas. |
| Comportamiento | Deterministas / probabilísticos | Se describen mediante reglas que fijan el resultado o mediante resultados con incertidumbre. |
| Tiempo | Estáticos / dinámicos | Se representan en un estado o mediante su evolución temporal. |

En termodinámica, «cerrado» no equivale a «aislado»: un sistema cerrado puede intercambiar energía. En el análisis de software conviene declarar explícitamente qué intercambios se consideran y dónde se coloca la frontera.

### 2.4. Elementos de un sistema (Q6)

Las **entradas** son los datos o recursos recibidos; el **proceso** los transforma, y las **salidas** son los resultados producidos. La **retroalimentación** devuelve información sobre esos resultados e influye en acciones posteriores; no siempre implica corregir o estabilizar el sistema, porque también puede reforzar un cambio.

El **entorno** comprende las condiciones externas que influyen en el sistema; la **frontera** delimita el alcance del análisis. Los **subsistemas** son partes que pueden estudiarse como sistemas, las **relaciones** conectan sus elementos y el **objetivo** orienta su diseño. Meadows (2008) sirve como referencia para el estudio de fronteras, retroalimentación y comportamiento sistémico.

### 2.5. Modelo y simulación (Q7 y Q8)

Un modelo es una representación simplificada que conserva los aspectos necesarios para responder una pregunta. Puede ser físico, matemático, gráfico, conceptual o computacional. Su utilidad depende de sus supuestos: una representación útil para una tarea puede ser insuficiente para otra.

Una simulación ejecuta un modelo para explorar su comportamiento sin intervenir directamente sobre el sistema real. Permite comparar escenarios y estudiar posibles resultados. El mapa menciona simulación discreta, continua y Monte Carlo; esta última se basa en muestreo aleatorio y no es una categoría excluyente de las otras dos. La simulación debe contrastarse con evidencia antes de usarla para predecir situaciones reales.

<!-- pagebreak -->

## 3. Aplicación a IHC y modelo matemático

### 3.1. Planteamiento del problema

Como ejemplo complementario, se propone una interfaz en la que un control permite elegir la intensidad de gris de un rectángulo. La aplicación debe recibir el valor solicitado, actualizar su estado y mostrar una respuesta visual. El objetivo es representar el ciclo entrada, proceso, salida y retroalimentación de una forma sencilla.

Se toma la aplicación como frontera del sistema: el usuario pertenece al entorno, el control proporciona la entrada y el rectángulo es la salida. Al observarlo y volver a mover el control, la persona cierra el ciclo de interacción. Este ejemplo no mide percepción de brillo, rendimiento ni usabilidad.

### 3.2. Variables y ecuaciones

Sea $u_k$ el valor solicitado por el usuario y $x_k$ el estado de intensidad normalizada en el paso $k$, con ambos valores entre 0 y 1. Sea $\alpha$ un factor de actualización, con $0 < \alpha \leq 1$. Una transición gradual puede modelarse así:

$$
x_{k+1}=x_k+\alpha(u_k-x_k).
$$

La diferencia $u_k-x_k$ expresa cuánto falta para alcanzar la entrada. El siguiente estado conserva una fracción del actual y avanza hacia el valor solicitado. Si $x_k$ y $u_k$ están en el intervalo indicado, el nuevo estado también permanece en ese intervalo.

Para representar el estado mediante un canal de color de ocho bits se propone:

$$
c_{k+1}=\operatorname{round}(255x_{k+1}),\qquad R=G=B=c_{k+1}.
$$

El valor de color representa una intensidad digital, no una medida física ni perceptual de luminosidad. Se supone un intervalo de actualización constante; con una tasa variable de cuadros, un factor fijo puede cambiar la velocidad aparente de la transición.

### 3.3. Ejemplo por sustitución

Para $x_0=0$, una entrada constante $u_k=1$ y $\alpha=0.25$:

$$
x_1=0+0.25(1-0)=0.25.
$$

$$
x_2=0.25+0.25(1-0.25)=0.4375.
$$

$$
x_3=0.4375+0.25(1-0.4375)=0.578125.
$$

Los canales de gris correspondientes son 64, 112 y 147, respectivamente. Son resultados aritméticos del modelo, no mediciones de una aplicación ejecutada. Con $\alpha=1$ la respuesta es inmediata; con un valor menor, el estado se aproxima gradualmente a la entrada.

<!-- pagebreak -->

## 4. Algoritmo y relación con la programación gráfica

El modelo puede traducirse en un ciclo de actualización y dibujo. El siguiente pseudocódigo expresa la secuencia; las operaciones de entrada, ventana y dibujo deberán implementarse si se desarrolla un programa posteriormente.

```text
x = 0
alpha = 0.25
mientras la ventana permanezca abierta:
    u = leer_control_normalizado()
    u = limitar(u, 0, 1)
    x = x + alpha * (u - x)
    c = redondear(255 * x)
    dibujar_rectangulo_con_color(c, c, c)
    presentar_cuadro()
```

En una implementación en C++, las variables conservarían el estado del modelo. Una biblioteca gráfica permitiría recibir eventos y dibujar la salida. La documentación debería explicar por separado la lectura del control, la actualización y la representación visual, así como las dependencias reales del programa.

Esta actividad no incorpora código ejecutable ni resultados de compilación. La separación anterior establece una ruta de desarrollo a partir del mapa conceptual: identificar el problema, modelar su comportamiento, formular un algoritmo y después construir y evaluar la implementación.

## 5. Conclusión

La teoría de sistemas permite estudiar una aplicación a partir de sus componentes y relaciones. El mapa conceptual organiza las ideas necesarias para distinguir el sistema, su entorno, sus entradas, sus procesos y sus salidas, además de reconocer el papel de los modelos y la simulación.

En IHC, este enfoque ayuda a conectar la acción de una persona con el cambio de estado de un programa y con la respuesta que aparece en pantalla. El ejemplo de intensidad de gris muestra cómo una descripción conceptual puede convertirse en una ecuación y luego en un algoritmo. Para evaluar una interfaz real todavía sería necesario implementar la propuesta, comprobar su funcionamiento y observar cómo la utilizan las personas.

<!-- pagebreak -->

## Referencias

Bertalanffy, L. von. (1968). *General system theory: Foundations, development, applications*. George Braziller.

Gonzalez Orozco, S. A. (2026, 3 de octubre). *Fundamentos de la teoría de sistemas / Fundamentals of systems theory* [Mapa conceptual bilingüe, trabajo de clase]. Universidad de Guadalajara.

Meadows, D. H. (2008). *Thinking in systems: A primer* (D. Wright, Ed.). Chelsea Green Publishing.

Senge, P. M. (1990). *The fifth discipline: The art and practice of the learning organization*. Doubleday/Currency.

### Enlaces de consulta bibliográfica

- Bertalanffy: [ficha editorial de General System Theory](https://www.georgebraziller.com/general-systems-theory). La página corresponde a una edición revisada; la referencia anterior conserva el año citado en el mapa.
- Meadows: [ficha editorial de Thinking in Systems](https://www.chelseagreen.com/product/thinking-in-systems/).
- Senge: [semblanza del autor y referencia a la publicación de 1990](https://www.solonline.org/peter-senge/).

Las referencias de los tres libros se desarrollaron a partir de las citas abreviadas del mapa. Los enlaces permiten consultar información editorial y bibliográfica; no se atribuyen citas textuales ni números de página a obras que no se revisaron íntegramente.

## Anexo. Evidencia original

El [mapa conceptual original en PDF](assets/mapa_conceptual_original.pdf) contiene los mapas en español e inglés y una nota personal sobre el aprendizaje del inglés. Se conserva completo como evidencia de la actividad; también se incluye una [vista en imagen](assets/mapa_conceptual_vista.png) para facilitar su consulta en GitHub.

**Nota de identificación:** el documento original muestra «Tech Reading 2» en el encabezado. Este reporte se identifica como **Writting 1** conforme a la indicación del estudiante. El PDF fuente permanece sin modificaciones.
