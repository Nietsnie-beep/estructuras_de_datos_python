# estructuras de datos lineales python

completado: Yes

### Github

[https://github.com/Nietsnie-beep/python_estructuras_de_datos_lineal.git](https://github.com/Nietsnie-beep/python_estructuras_de_datos_lineal.git)

```python
head = None

class Node():
    def __init__(self,data, next=None): 
#el ultimo nodo no lleva a ningun lado
        
        self.data = data
        self.next = next

node1 = Node('c', None)
node2 = Node('A', node1)
node3 = Node('B', node2)

#create Nodes with numbers 1 to 5 in head(id)
for count in range(1,5):
    head = Node(count,head)

while head != None:
    print (head.data)
    head = head.next
```

### Nodes y singly linked list

Las estructuras linked consisten en nodos conectados a otros, los más comunes son sencillos o dobles. No se accede por índice sino por recorrido. Es decir se busca en la lista de nodos hasta encontrar un valor.

- **Data**: Será el valor albergado en un nodo.
- **Next**: Es la referencia al siguiente nodo en la lista
- **Previous**: Será el nodo anterior.
- **Head**: Hace referencia al primer nodo en la lista
- **Tail**: Hace referencia al último nodo.

```python
from node import Node

class SinglyLinkedList():
    def __init__(self):
        self.tail = None
        self.size = 0
   
    def append(self, data):

        node = Node(data)

        if self.tail == None:
            self.tail = node
            
        else:
            current = self.tail #current == actual

            while current.next:
                current = current.next

            current.next = node
        
        self.size += 1
    
    def add(self):
        #* Agregar un nuevo elemento/nodo por "indice" inverso(Cuenta de Head - Tail)
        new_item = input("Enter new item: ")
        index = int(input("Enter the position to insert the new item: "))
    
        head = self.tail
        
        if head is None or index <= 0:
            head = Node(new_item, head)
        else:
            probe = head
            while index > 1 and probe.next != None:
                probe = probe.next
                index -= 1
            probe.next = Node(new_item, probe.next)
                        
    def sizer(self):
        return str(self.size)

    def iter(self):
        current = self.tail

        while current:
            val = current.data
            current = current.next
            yield val

    def delete(self, data):
        current = self.tail
        previous = self.tail

        while current:
            if current.data == data:
                if current == self.tail:
                    self.tail = current.next
            
                else:
                    previous.next = current.next
                    self.size -=1
                    return current.data

            previous =  current
            current = current.next

    def search(self, data):
        for node in self.iter():
            if data == node:
                print(f'data {data} found!')

    def clear(self):
        self.tail = None
        self.head = None
        self.size = 0
```

Una **lista enlazada simple** es un tipo de lista enlazada que es *unidireccional* , es decir, se puede recorrer en una sola dirección desde la cabeza hasta el último nodo (cola).

Cada elemento de una lista enlazada se denomina **nodo** . Un solo nodo contiene *datos* y un puntero al *siguiente* nodo que ayuda a mantener la estructura de la lista.

El primer nodo se llama **cabeza** ; apunta al primer nodo de la lista y nos ayuda a acceder a todos los demás elementos de la lista. El último nodo, también llamado **cola** , apunta a *NULL* , lo que nos ayuda a determinar cuándo termina la lista.

![descarga.svg](estructuras%20de%20datos%20lineales%20python%2088bd02c58fa84a4e8faaabbb13bffcef/descarga.svg)

****Operaciones comunes de listas enlazadas individualmente:****

## **Buscar un nodo en la Lista**

Puede determinar y recuperar un nodo específico desde el frente, el final o en cualquier lugar de la lista.

***La Complejidad de tiempo*** en el peor de los casos para recuperar un nodo de cualquier parte de la lista es *O(n)* .

![buscar.svg](estructuras%20de%20datos%20lineales%20python%2088bd02c58fa84a4e8faaabbb13bffcef/buscar.svg)

### **Agregar un nodo a la Lista**

Puede agregar un nodo al frente, al final o en cualquier lugar de la lista vinculada.

***La Complejidad de Tiempo*** en el peor de los casos para realizar estas operaciones es la siguiente:

- Agregar elemento al frente de la lista: O(1)
- Añadir elemento al final de la lista: O(n)
- Agregar elemento a cualquier parte de la lista: O(n)

![Untitled](estructuras%20de%20datos%20lineales%20python%2088bd02c58fa84a4e8faaabbb13bffcef/Untitled.png)

****Eliminar un nodo de la lista****

![eliminar.svg](estructuras%20de%20datos%20lineales%20python%2088bd02c58fa84a4e8faaabbb13bffcef/eliminar.svg)

Puede eliminar un nodo desde el frente, el final o desde cualquier lugar de la lista.

***La Complejidad de Tiempo*** en el peor de los casos para realizar esta operación es la siguiente:

- Eliminar elemento del frente de la lista: O(1)
- Eliminar elemento del final de la lista: O(n)
- Eliminar elemento de cualquier parte de la lista: O(n)

---

**¿Cómo funciona en memoria los Linked Estructures?**

Estas estructuras de datos hablan de `nodos/datos` repartidos en memoria, diferentes a los arrays que son contiguos. Los nodos se conectan a diferentes espacios en memoria, podemos acceder a los datos saltando en memoria, siendo mucho más ágil. Los nodos nos sirven para crear otras estructuras más complejas, como **Stacks, Queues**, las llamadas pilas y colas. Es posible optimizar partes del código usando nodos.

---

### **Double Linked Structure**.

Estos hacen que el nodo haga referencia al siguiente nodo y al anterior, es decir nos va a permitir ir en ambas direcciones. También nos permitirá realizar “formas” y contextos circulares.

- El ejemplo clave aquí será función de `ctrl+z` y `ctrl+y` Estas opciones nos permiten hacer y deshacer un proceso en Windows.
- El historial del navegador también es un buen ejemplo al permitirnos navegar entre el pasado y el presente.

---

## Queques

Conceptos importantes

se basa en fifo con elementos de mayor/menor prioridad.

### operacion fundamentales

- pop(): remover front
- add(): anadir a rear

![¿Qué son las queues_ - Platzi - Brave 31_05_2022 04_54_11 p. m..png](estructuras%20de%20datos%20lineales%20python%2088bd02c58fa84a4e8faaabbb13bffcef/Qu_son_las_queues__-_Platzi_-_Brave_31_05_2022_04_54_11_p._m..png)

![¿Qué son las queues_ - Platzi - Brave 31_05_2022 04_55_36 p. m..png](estructuras%20de%20datos%20lineales%20python%2088bd02c58fa84a4e8faaabbb13bffcef/Qu_son_las_queues__-_Platzi_-_Brave_31_05_2022_04_55_36_p._m..png)

---

## Pilas (Stacks)

Las pilas (stacks) son una estructura de datos donde tenemos una colección de elementos, y sólo podemos hacer dos cosas:

- añadir un elemento al final de la pila
- sacar el último elemento de la pila

Una manera común de visualizar una pila es imaginando una torre de panqueques, donde una vez que ponemos un panqueque encima de otro, no podemos sacar el anterior hasta que se hayan sacado todos los que están encima.

![https://miro.medium.com/max/700/1*qcjbuSJ4rf7VcFFFoDbc5Q.png](https://miro.medium.com/max/700/1*qcjbuSJ4rf7VcFFFoDbc5Q.png)

A pesar de su simplicidad, las pilas son estructuras relativamente comunes en ciertas áreas de la computación, en especial para implementar o simular evaluación de expresiones, recursión, scope, …

---

## LIFO (Last In First Out)

Las pilas son estructuras de tipo LIFO, lo cual quiere decir que el último elemento añadido es siempre el primero en salir.

De alguna forma, podemos decir que una pila es como si fuera una lista o array, en el sentido que es una colección, pero a diferencia de los arrays y otras colecciones, en las pilas solo accedemos al elemento que esté “encima de la pila”, el último elemento. Nunca manipulamos ni accedemos a valores por debajo del último elemento.

---

## Recomendaciones

+linked list = +complejo

cuantos hay en un stack? > true = usar array

pocos elementos nodos

fifo

queue