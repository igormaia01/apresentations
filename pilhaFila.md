---
theme: "blood"
transition: "none"
title: "Pilha e Fila em C++"
enableMenu: true
enableSearch: false
enableChalkboard: true
slideNumber: true
---
![-](https://www.educative.io/v2api/editorpage/6022915262251008/image/4991336293335040)

---

#### Estrutura de dados

Estrutura de dados é um conceito fundamental na ciência da computação que se refere à organização, armazenamento e manipulação de dados de forma eficiente. Uma estrutura de dados é escolhida com base nos requisitos do problema e na eficiência esperada das operações realizadas sobre os dados.

---

#### ADTS

Os Tipos Abstratos de Dados (ADTs - Abstract Data Types) são uma abstração que define um conjunto de operações possíveis em um tipo de dado, sem especificar sua implementação interna. O ADT descreve o comportamento esperado do tipo de dado, incluindo as operações permitidas e as restrições associadas a essas operações.

---

#### Fila

Uma fila é uma estrutura de dados que segue a política "primeiro a entrar, primeiro a sair" (FIFO - First-In-First-Out). Em uma fila, os elementos são inseridos no final e removidos do início, mantendo a ordem original de entrada. É como uma fila de pessoas, onde a primeira pessoa a entrar é a primeira a sair.

![fila.webp](https://images2.imgbox.com/ec/29/jOZo2bJZ_o.png)

---

#### Pilha

Uma pilha é uma estrutura de dados que segue a política "último a entrar, primeiro a sair" (LIFO - Last-In-First-Out). Em uma pilha, os elementos são inseridos e removidos apenas em uma extremidade, chamada topo da pilha. É como uma pilha de pratos, onde o último prato colocado é o primeiro a ser retirado.

![pilha2.jpg](https://thumbs2.imgbox.com/81/0c/NndWCH1r_t.png)

---

###### Implementação de uma fila utilizando vector em c++

```c++
#include <iostream>
#include <vector>

using namespace std;

class Fila
{
private:
  vector<int> elementos;

public:
  bool vazia()
  {
    return elementos.empty();
  }

  void enfileirar(int numero)
  { // push
    elementos.push_back(numero);
  }

  void desinfileirar()
  {
    if (vazia())
    {
      cout << "A fila esta vazia" << endl;
      return;
    }
    elementos.erase(elementos.begin()); // pop
  }

  int frenteDaFila()
  {
    if (vazia())
    {
      cout << "A fila esta vazia" << endl;
      return -1;
    }

    return elementos.front();
  }
};

int main()
{
  Fila fila;

  fila.enfileirar(1);
  fila.enfileirar(2);
  fila.enfileirar(3);

  cout << "Elemento da frente: " << fila.frenteDaFila() << endl;

  fila.desinfileirar();

  cout << "Elemento da frente apos desenfileirar: " << fila.frenteDaFila() << endl;

  fila.desinfileirar();

  cout << "Elemento da frente apos desenfileirar: " << fila.frenteDaFila() << endl;
}
```

---

#### Implemente uma pilha em C++ utilizando vector

```c++
#include <iostream>
#include <vector>

using namespace std;

class Pilha {
private:
   vector<int> elementos;

public:
    bool vazia() {
    }

    void empilhar(int elemento) {
    }

    void desempilhar() {
    }

    int topo() {
    }
};

int main() {
    Pilha pilha;

   
    return 0;
}
```

---

#### Utilizando libs do c++ para fila e pilha

```c++
#include <iostream>
#include <stack>
#include <queue>

using namespace std;

int main()
{
  cout << "Inserindo elemento  1 2 3  respectivamente na pilha e na fila" << endl;
  stack<int> myStack;
  myStack.push(1);
  myStack.push(2);
  myStack.push(3);

  cout << "Pilha" << endl;
  while (!myStack.empty())
  {
    int topElement = myStack.top();
    cout << "Elemento: " << topElement << endl;

    myStack.pop();
  }

  queue<int> myQueue;

  myQueue.push(1);
  myQueue.push(2);
  myQueue.push(3);

  cout << "Fila" << endl;

  while (!myQueue.empty())
  {
    int frontElement = myQueue.front();
    cout << "Elemento: " << frontElement << endl;

    myQueue.pop();
  }

  return 0;
}
```
---

#### Questão Beecrowd

[https://www.beecrowd.com.br/judge/pt/problems/view/1068](https://www.beecrowd.com.br/judge/pt/problems/view/1068)