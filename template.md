# Projeto LOGIN

Documentação de um **Nome do projeto** usando **BDD** (Behavior-Driven Development)

### Estrutura da Documentação para um **Nome do projeto** com BDD

1. [**Visão Geral**](#visao-geral)
2. [**Requisitos**](#requisitos)
3. [**Funcionalidades**](#funcionalidades)
4. [**Cenários de Teste (Feature Files)**](#cenarios-de-teste-feature-files)
5. [**Como Rodar os Testes**](#como-rodar-os-testes)
6. [**Conclusão**](#conclusao)

---

### 1. **Visão Geral**

Este documento descreve os requisitos e os testes automatizados do processo de **Nome do projeto** para o sistema. O site de login permite que os usuários acessem suas contas através de um nome de usuário e senha.

#### Objetivo:
Garantir que o sistema de **Nome do projeto** funcione conforme os critérios de aceitação definidos, assegurando a experiência do usuário ao fazer login de forma segura e eficaz.

### 2. **Requisitos**

**Funcionalidade do Sistema**:
- ** **: O sistema 

### 3. **Funcionalidades**

- **Funcionalidade 1**
  - Descrição da funcionalidade

- **Funcionalidade 2**
  - Descrição da funcionalidade

- **Funcionalidade 3**
  - Descrição da funcionalidade

- **Validação**
  - |Descrição da validação

  Cenários propostos:

    - Cenário 1
    - Cenário 2
    - Cenário 3

---

### 4. **Cenários de Teste (Feature Files)**

A seguir, são apresentados os cenários de teste utilizando **Gherkin**, a linguagem padrão para especificações de BDD, que descrevem o comportamento esperado do sistema.

#### Arquivo: `login.feature`

```gherkin
Feature: Nome da FEATURE

  Como um usuário do sistema
  Eu quero realizar ...

  Scenario: Nome do cenário
    Dado que eu estou na página
    Quando eu 
    E clico no botão
    Então eu devo receber a mensagem ...  

```

#### Explicação dos Cenários:
1. **Cenário: Descrição do cenario**

    Testa o comportamento do sistema "


---

### 5. **Como Rodar os Testes**
Os testes podem ser executados utilizando ferramentas como:
    - Robotframework
    - Playwrite

#### Passos para rodar os testes:

1. **Pré-requisitos**:

Certifique-se de que você tem o **PIP** e **Python** instalados.

Instale as dependências necessárias:

- Para **Robotframework**:
        
```bash
pip install robotframework
```
- Para **Playwright**:

```bash
pip install playwright       
```
Instale o driver para o navegador de sua escolha (ChromeDriver, GeckoDriver, etc.).

```bash
       
```

2. **Estrutura do Projeto**:
   - **features**: Diretório onde os arquivos `.feature` são armazenados.
   - **steps**: Diretório onde as definições dos passos são implementadas.

3. **Executar os testes**:

- Para **Robotframework**:
```bash
robot testes/
```

- Para **Playwrite**:

```bash
python run_tests.py
```

4. **Verificação dos Resultados**:
    Após a execução, verifique se todos os cenários passaram. Em caso de falhas, revise os logs e faça os ajustes necessários.

5. **Evidências dos testes realizados**:
    Os resultados dos testes estarão em uma pasta chamada **Results** com os cenários devidamente sepadaros.
---

### 6. **Conclusão**

Este documento descreve como implementar testes automatizados para a funcionalidade de login de um site utilizando BDD. O **Gherkin** foi utilizado para escrever os cenários de teste de forma legível, permitindo uma comunicação clara entre desenvolvedores e stakeholders. O uso de ferramentas como **Robotframework** ou **Playwrite** permite a execução automatizada desses cenários, garantindo que o sistema de login funcione conforme o esperado.

---

### Documentação BDD:

- **Facilidade de Leitura**: Mantenha os cenários simples e legíveis, utilizando uma linguagem que todos os envolvidos no projeto possam entender, incluindo desenvolvedores, testers e até clientes.
- **Compreensão das Regras de Negócio**: A documentação BDD deve refletir as regras de negócio e o comportamento esperado de forma clara.
- **Manutenção de Testes**: Sempre que o comportamento do sistema mudar, revise os cenários para garantir que os testes permaneçam relevantes.

Essa abordagem permite que todos os envolvidos no desenvolvimento compreendam como o sistema deve se comportar em diferentes cenários, e como testar esses comportamentos de maneira eficaz.