# 🏦 Sistema Bancário - Conta Bancária

## 🎯 Objetivo de Aprendizado
Projeto desenvolvido para estudar **Programação Orientada a Objetos (POO)** em Java, implementando um sistema bancário completo com conceitos fundamentais como herança, polimorfismo, encapsulamento e abstração.

## 🛠️ Tecnologias Utilizadas
- **Linguagem:** Java 17+
- **Paradigma:** Programação Orientada a Objetos
- **Estruturas:** Collections (ArrayList)
- **Padrões:** Repository Pattern, MVC
- **Conceitos estudados:** 
  - Classes abstratas e herança
  - Polimorfismo e sobrescrita de métodos
  - Encapsulamento com getters/setters
  - Collections e manipulação de dados

## 🚀 Demonstração
```
************************************************************************
                      BANCO DO BRAZIL COM Z                            
************************************************************************
        1 - Criar Conta
        2 - Listar todas as contas
        3 - Buscar conta por Número
        4 - Atualizar Dados da Conta
        5 - Apagar Conta
        6 - Sacar
        7 - Depositar
        8 - Transferir Valor entre Contas
        9 - Sair
************************************************************************
```

## 💡 Principais Aprendizados

### 🏗️ Arquitetura MVC
- **Model:** Classes `Conta`, `ContaCorrente`, `ContaPoupanca`
- **View:** Interface de menu no console
- **Controller:** `ContaController` gerenciando operações

### 🔄 Conceitos de POO Aplicados
- **Herança:** `ContaCorrente` e `ContaPoupanca` herdam de `Conta`
- **Polimorfismo:** Método `sacar()` sobrescrito na conta corrente
- **Encapsulamento:** Atributos privados com métodos de acesso
- **Abstração:** Classe `Conta` como base abstrata

### 📊 Funcionalidades Implementadas
- ✅ Criação de contas (Corrente e Poupança)
- ✅ Operações bancárias (saque, depósito, transferência)
- ✅ Busca e listagem de contas
- ✅ Validação de saldo e limites
- ✅ Interface colorida no terminal

## 🔧 Como Executar

### Pré-requisitos
- Java JDK 17 ou superior
- IDE (Eclipse, IntelliJ, VS Code)

### Passos
1. Clone o repositório:
```bash
git clone <repo-url>
cd contabancaria
```

2. Compile o projeto:
```bash
javac -d bin src/conta/*.java src/conta/*/*.java
```

3. Execute a aplicação:
```bash
java -cp bin conta.Menu
```

## 📁 Estrutura do Projeto
```
contabancaria/
├── src/
│   └── conta/
│       ├── Menu.java              # Classe principal com interface
│       ├── controller/
│       │   └── ContaController.java   # Lógica de negócio
│       ├── model/
│       │   ├── Conta.java            # Classe abstrata base
│       │   ├── ContaCorrente.java    # Conta com limite
│       │   └── ContaPoupanca.java    # Conta com aniversário
│       ├── repository/
│       │   └── ContaRepository.java  # Interface do repositório
│       └── util/
│           └── Cores.java           # Utilitário para cores no terminal
├── bin/                           # Classes compiladas
└── .github/workflows/
    └── sonar.yml                 # CI/CD com SonarQube
```

## 🧠 Conceitos Técnicos Estudados

### 1. **Classes Abstratas**
```java
public abstract class Conta {
    // Atributos comuns a todas as contas
    private int numero, agencia, tipo;
    private String titular;
    private float saldo;
    
    // Método que pode ser sobrescrito
    public boolean sacar(float valor) { ... }
}
```

### 2. **Herança e Polimorfismo**
```java
public class ContaCorrente extends Conta {
    private float limite;
    
    @Override
    public boolean sacar(float valor) {
        // Permite saque até o limite + saldo
        if(this.getSaldo() + this.limite < valor) {
            return false;
        }
        this.setSaldo(this.getSaldo() - valor);
        return true;
    }
}
```

### 3. **Repository Pattern**
```java
public interface ContaRepository {
    public void procurarPorNumero(int numero);
    public void listarTodas();
    public void cadastrar(Conta conta);
    public void atualizar(Conta conta);
    public void deletar(int numero);
}
```

## 📈 Próximos Passos
- [ ] Implementar persistência em banco de dados
- [ ] Adicionar testes unitários com JUnit
- [ ] Criar interface gráfica com JavaFX
- [ ] Implementar autenticação de usuários
- [ ] Adicionar relatórios de movimentação
- [ ] Integrar com API REST

## 🚧 Desafios Enfrentados
1. **Validação de entrada:** Tratamento de `InputMismatchException`
2. **Polimorfismo:** Entender quando sobrescrever métodos
3. **Collections:** Manipular ArrayList para busca e remoção
4. **Interface de usuário:** Criar menu intuitivo no console

## 📚 Recursos Utilizados
- [Documentação Oracle Java](https://docs.oracle.com/javase/17/)
- [Tutorial POO em Java - Generation Brasil](https://github.com/conteudoGeneration)
- [Padrões de Projeto em Java](https://refactoring.guru/design-patterns/java)
- [Collections Framework](https://docs.oracle.com/javase/tutorial/collections/)

## 🔗 Projetos Relacionados
- [Spring E-commerce](../spring-ecommerce-tt/) - Evolução para web com Spring Boot
- [Java Generation Notes](../java-generation-notes/) - Anotações de estudo Java
- [Spring Blog Platform](../spring-blog-platform/) - Aplicação web completa

---

**Desenvolvido por:** Felipe Macedo  
**Contato:** contato.dev.macedo@gmail.com  
**GitHub:** [FelipeMacedo](https://github.com/felipemacedo1)  
**LinkedIn:** [in/felipemacedo1](https://linkedin.com/in/felipemacedo1)

> 💡 **Reflexão:** Este projeto foi fundamental para consolidar os conceitos de POO em Java. A implementação de herança e polimorfismo no contexto bancário tornou os conceitos mais tangíveis e práticos.