## Sistema de Gerenciamento de Biblioteca - UML

Este diagrama UML representa o sistema de gerenciamento de biblioteca, com a implementação dos conceitos de classes, herança, propriedade, encapsulamento e classes abstratas.

**Classes:**

* **ItemBiblioteca:** Classe abstrata que representa um item da biblioteca (livro, revista, etc).
    * Atributos:
        * Título (String)
    * Métodos:
        * ObterTítulo(): String
* **Livro:** Classe que herda de ItemBiblioteca.
    * Atributos:
        * Editora (String)
        * Gêneros (Lista de String)
        * ExemplaresDisponíveis (Lista de Exemplar)
        * NúmeroMaximoRenovações (Inteiro, opcional)
    * Métodos:
        * AdicionarAutor (Autor)
        * RemoverAutor (Autor)
        * AdicionarGenero (String)
        * RemoverGenero (String)
        * EmprestarExemplar (Exemplar)
        * DevolverExemplar (Exemplar)
        * ObterAutores() : Lista de Autor
        * ObterGeneros() : Lista de String
        * ObterExemplaresDisponíveis() : Lista de Exemplar
        * ObterNúmeroMaximoRenovações(): Inteiro (opcional)
* **Autor:**
    * Atributos:
        * Nome (String)
    * Métodos:
        * ObterNome() : String
* **Exemplar:**
    * Atributos:
        * ID (Inteiro)
        * Estado (Enum: Emprestado, Devolvido)
        * DataEmprestimo (Data, opcional)
        * DataDevolução (Data, opcional)
        * Livro (Livro)
    * Métodos:
        * Emprestar (Usuário, Data)
        * Devolver (Data)
* **Usuário:**
    * Atributos:
        * Nome (String)
        * Telefone (String)
        * Nacionalidade (String)
    * Métodos:
        * ObterNome() : String
        * ObterTelefone() : String
        * ObterNacionalidade() : String
* **Empréstimo:**
    * Atributos:
        * DataEmprestimo (Data)
        * DataDevolução (Data, opcional)
        * Estado (Enum: Emprestado, Devolvido)
        * Exemplar (Exemplar)
        * Usuário (Usuário)
    * Métodos:
        * Renovar (Data)
        * Devolver (Data)

**Relações:**

* **ItemBiblioteca - Livro:** Herança. Livro é um tipo específico de ItemBiblioteca.
* **Livro - Autor:** Uma relação de *um para muitos*. Um livro pode ter um ou mais autores, e um autor pode escrever vários livros.
* **Livro - Exemplar:** Uma relação de *um para muitos*. Um livro pode ter vários exemplares, e um exemplar pertence a um único livro.
* **Exemplar - Empréstimo:** Uma relação de *um para um*. Um exemplar pode estar associado a um único empréstimo, e um empréstimo é associado a um único exemplar.
* **Empréstimo - Usuário:** Uma relação de *um para um*. Um empréstimo é feito por um único usuário, e um usuário pode ter vários empréstimos.

**Encapsulamento:**

* Os atributos de cada classe são privados, acessíveis apenas através de métodos públicos (getters e setters).
* Os métodos da classe controlam a forma como os atributos são modificados e acessados.

**Herança:**

* A classe Livro herda da classe ItemBiblioteca, reutilizando os atributos e métodos da classe base.
* A classe ItemBiblioteca é uma classe abstrata, que define uma estrutura comum para itens da biblioteca.

**Diagrama:**

```mermaid
classDiagram
  ItemBiblioteca <|.. Livro
  Livro --|> Exemplar
  Livro --|> Autor
  Livro --|> Empréstimo
  Exemplar --|> Empréstimo
  Empréstimo --|> Usuário
  
  ItemBiblioteca : +Título : String
  ItemBiblioteca : +ObterTítulo() : String
  
  Livro : +Editora : String
  Livro : +Gêneros : Lista de String
  Livro : +ExemplaresDisponíveis : Lista de Exemplar
  Livro : +NúmeroMaximoRenovações : Inteiro
  Livro : +AdicionarAutor(Autor)
  Livro : +RemoverAutor(Autor)
  Livro : +AdicionarGenero(String)
  Livro : +RemoverGenero(String)
  Livro : +EmprestarExemplar(Exemplar)
  Livro : +DevolverExemplar(Exemplar)
  Livro : +ObterAutores() : Lista de Autor
  Livro : +ObterGeneros() : Lista de String
  Livro : +ObterExemplaresDisponíveis() : Lista de Exemplar
  Livro : +ObterNúmeroMaximoRenovações(): Inteiro
  
  Autor : +Nome : String
  Autor : +ObterNome() : String
  
  Exemplar : +ID : Inteiro
  Exemplar : +Estado : Enum (Emprestado, Devolvido)
  Exemplar : +DataEmprestimo : Data
  Exemplar : +DataDevolução : Data
  Exemplar : +Livro : Livro
  Exemplar : +Emprestar(Usuário, Data)
  Exemplar : +Devolver(Data)
  
  Usuário : +Nome : String
  Usuário : +Telefone : String
  Usuário : +Nacionalidade : String
  Usuário : +ObterNome() : String
  Usuário : +ObterTelefone() : String
  Usuário : +ObterNacionalidade() : String
  
  Empréstimo : +DataEmprestimo : Data
  Empréstimo : +DataDevolução : Data
  Empréstimo : +Estado : Enum (Emprestado, Devolvido)
  Empréstimo : +Renovar(Data)
  Empréstimo : +Devolver(Data)
```

**Observações:**

* O diagrama UML demonstra a estrutura básica do sistema, não incluindo detalhes específicos de implementação.
* A classe ItemBiblioteca serve como base para outros tipos de itens da biblioteca, garantindo a reutilização de código.
* O encapsulamento garante a proteção dos atributos de cada classe e a organização do código.
* A relação de herança entre ItemBiblioteca e Livro permite a criação de um sistema mais flexível e reutilizável.
* O diagrama UML serve como um guia para o desenvolvimento do sistema de gerenciamento de biblioteca, mostrando a estrutura e as relações entre as classes.

