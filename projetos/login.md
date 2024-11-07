# Projeto LOGIN

Documentação de um **site de login** usando **BDD** (Behavior-Driven Development)

### Estrutura da Documentação para um Site de Login com BDD

1. [**Visão Geral**](#visao-geral)
2. [**Requisitos**](#requisitos)
3. [**Funcionalidades**](#funcionalidades)
4. [**Cenários de Teste (Feature Files)**](#cenarios-de-teste-feature-files)
5. [**Como Rodar os Testes**](#como-rodar-os-testes)
6. [**Conclusão**](#conclusao)

---

### 1. **Visão Geral**

Este documento descreve os requisitos e os testes automatizados do processo de **login** para o sistema. O site de login permite que os usuários acessem suas contas através de um nome de usuário e senha.

#### Objetivo:
Garantir que o sistema de login funcione conforme os critérios de aceitação definidos, assegurando a experiência do usuário ao fazer login de forma segura e eficaz.

### 2. **Requisitos**

**Funcionalidade do Sistema de Login**:
- **Página de Login**: O sistema oferece um formulário para os usuários inserirem seu nome de usuário e senha.
- **Validação de Login**: O sistema valida as credenciais e permite o acesso se forem corretas. Caso contrário, exibe uma mensagem de erro.
- **Recuperação de Senha**: O sistema permite ao usuário recuperar a senha, enviando um link de recuperação para o e-mail cadastrado.

### 3. **Funcionalidades**

- **Página de Login**
  - O usuário deve ser capaz de acessar uma página de login.
  - Campos necessários: `Nome de usuário` e `Senha`.
  - Botão de ação: `Entrar`.

- **Validação de Login**
  - O sistema deve validar se as credenciais são corretas.
  - Se forem, o sistema deve redirecionar o usuário para a página principal.
  - Se as credenciais forem inválidas, o sistema deve exibir uma mensagem de erro como "Usuário ou senha inválidos".

  Cenários propostos:

    - Campos vazios (Usuário tenta acessar o site sem preencher os campos e recebe uma mensagem "E-mail e senha são obrigatórios!".)
    - E-mail Válido e Senha Inválida (Usuário tenta acessar o site passando um e-mail válido mas com a senha inválida)
    - E-mail Inválido e Senha Válida (Usuário tenta acessar o site passando um e-mail inválido mas com a senha válida)
    - Ambos Inválidos (Usuário tenta acessar o site passando um e-mail e senha inválidos)
    - Ambos Válidos (Usuário tenta acessar o site passando um e-mail e senha válidos)

- **Recuperação de Senha**
    - O usuário deve poder clicar no link **"Esqueci minha senha"**.
    - Após inserir o e-mail registrado, o usuário deve receber um link para redefinir sua senha.

- **Logout**
    - O usuário estando em qualquer página logada, e clicar no link **"LOGOUT"** deve ser redirecionado para a página de login.

---

### 4. **Cenários de Teste (Feature Files)**

A seguir, são apresentados os cenários de teste utilizando **Gherkin**, a linguagem padrão para especificações de BDD, que descrevem o comportamento esperado do sistema.

#### Arquivo: `login.feature`

```gherkin
Feature: Login no sistema

  Como um usuário do sistema
  Eu quero realizar o login usando meu nome de usuário e senha
  Para poder acessar minha conta de forma segura.

  Scenario: Login com credenciais vazias
    Dado que eu estou na página de login
    Quando eu não preencho o nome de usuário com "usuario_teste" e a senha com "senha_segura"
    E clico no botão de "Entrar"
    Então eu devo receber a mensagem "Os campos são obrigatórios"
  
  Scenario: Login com credenciais inválidas - E-mail correto, senha errada.
    Dado que eu estou na página de login
    Quando eu preencho o nome de usuário com "usuario@example.com" e a senha com "abcd1234"
    E clico no botão de "Entrar"
    Então eu devo receber a mensagem "E-mail ou senha inválidos"
  
  Scenario: Login com credenciais inválidas - E-mail errado, senha correta.
    Dado que eu estou na página de login
    Quando eu preencho o nome de usuário com "usuarioexample.com" e a senha com "1q2w3e4r"
    E clico no botão de "Entrar"
    Então eu devo receber a mensagem "E-mail ou senha inválidos"

  Scenario: Login com credenciais inválidas - E-mail e senha errados.
    Dado que eu estou na página de login
    Quando eu preencho o nome de usuário com "usuarioexample.com" e a senha com "abcd1234"
    E clico no botão de "Entrar"
    Então eu devo ver uma mensagem de erro "Usuário ou senha inválidos"

  Scenario: Login com credenciais válidas
    Dado que eu estou na página de login
    Quando eu preencho o nome de usuário com "usuario@example.com" e a senha com "1q2w3e4r"
    E clico no botão de "Entrar"
    Então eu devo ser redirecionado para a página seguinte

  Scenario: Recuperação de senha
    Dado que eu estou na página de login
    Quando eu clico no link "Esqueci minha senha"
    E preencho meu e-mail "usuarioexample.com"
    E clico em "Enviar link de recuperação"
    Então eu devo receber um link para redefinir minha senha no meu e-mail

  Scenario: Acesso a página de login a partir de qualquer página
    Dado que eu estou em qualquer página do sistema
    Quando eu clico no link de "Logout"
    Então eu sou redirecionado para a página de login
```

#### Explicação dos Cenários:
1. **Cenário: Login com credenciais vazias**

    Testa o comportamento do sistema quando os campos das credenciais não são preenchidas. O sistema deve exibir uma mensagem de erro. "Os campos são obrigatórios"

2. **Cenário: Login com credenciais inválidas - E-mail correto, senha errada**
    
    Testa o comportamento do sistema quando as credenciais fornecidas são inválidas. O sistema deve exibir uma mensagem de erro.

3. **Cenário: Login com credenciais inválidas - E-mail errado, senha correta.**
    
    Testa o comportamento do sistema quando as credenciais fornecidas são inválidas. O sistema deve exibir uma mensagem de erro.

4. **Cenário:Login com credenciais inválidas - E-mail e senha errados.**
    
    Testa o comportamento do sistema quando as credenciais fornecidas são inválidas. O sistema deve exibir uma mensagem de erro.

5. **Cenário: Login com credenciais válidas**
    
    Testa o login com um nome de usuário e senha válidos. O sistema deve permitir o acesso à página principal.

6. **Cenário: Recuperação de senha**
    Testa o fluxo de recuperação de senha, onde o usuário insere seu e-mail e recebe um link para redefinir sua senha.

7. **Cenário: Acesso à página de login após logout**
    
    Testa o comportamento do sistema quando o usuário tenta acessar a página de login após sair do sistema.


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