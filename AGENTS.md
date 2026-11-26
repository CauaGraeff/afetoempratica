# AGENTS.md — Regras e Diretrizes do Projeto

## 1. Instruções Gerais

Este documento define as regras, padrões e diretrizes obrigatórias para o desenvolvimento deste projeto.

> **REGRA OBRIGATÓRIA:** Antes de executar qualquer tarefa, escrever código, modificar arquivos ou tomar decisões arquiteturais, o agente de IA **DEVE** ler integralmente este documento e seguir todas as instruções nele estabelecidas.

O agente deverá:
- Seguir todas as regras estabelecidas neste documento.
- Manter consistência com a arquitetura existente.
- Priorizar código limpo, legível, organizado e escalável.
- Evitar complexidade desnecessária e duplicação de código.
- Não adicionar tecnologias ou dependências sem justificativa.
- Analisar o código existente antes de realizar modificações.
- Evitar alterações em funcionalidades não relacionadas à tarefa solicitada.
- Informar ao usuário quando identificar conflitos entre requisitos e regras.

---

## 2. Regras de Idioma

### 2.1. Comunicação com o usuário
Toda comunicação do agente deverá ser realizada em **português brasileiro (PT-BR)**. Isso inclui:
- Explicações sobre implementações.
- Respostas às dúvidas.
- Sugestões técnicas.
- Relatórios de alterações.
- Explicações de erros.
- Resumos de tarefas.

### 2.2. Código-fonte
Os identificadores do código deverão ser escritos **exclusivamente em inglês**. Isso inclui:
- Nomes de variáveis.
- Nomes de métodos e funções.
- Nomes de classes e interfaces.
- Nomes de componentes.
- Nomes de constantes.
- Nomes de arquivos e diretórios.
- Nomes de propriedades e atributos personalizados.

Comentários e documentações dentro do código deverão ser escritos em **português brasileiro**. Isso inclui:
- Comentários de linha.
- Comentários de bloco.
- Documentação de métodos e classes.
- Explicações sobre regras de negócio.
- Comentários sobre implementações complexas.

**Exemplo correto:**

```java
/**
 * Busca um usuário pelo seu identificador.
 *
 * @param userId identificador do usuário
 * @return usuário encontrado
 */
public User findUserById(Long userId) {
    // Busca o usuário no banco de dados
    return userRepository.findById(userId)
        .orElseThrow(() -> new UserNotFoundException());
}
```

> **Regra:** Não misturar português e inglês nos identificadores. Identificadores devem permanecer em inglês e comentários em português.

---

## 3. Tecnologias Obrigatórias

### 3.1. Frontend
- **React:** biblioteca para desenvolvimento da interface do usuário.
- **JavaScript (ES6+):** linguagem de programação obrigatória para o desenvolvimento frontend.
- **HTML5:** estruturação semântica das páginas.
- **CSS3:** estilização das interfaces.

**Regras adicionais:**
- Não utilizar TypeScript no projeto.
- Utilizar JavaScript moderno (ES6+).
- Utilizar componentes funcionais do React.
- Utilizar React Hooks adequadamente.
- Priorizar código semântico, organizado e reutilizável.

### 3.2. Backend
- **Java 21:** linguagem de programação.
- **Spring Boot:** framework para desenvolvimento do backend.
- **Spring Data JPA:** gerenciamento da persistência de dados.
- **Maven:** gerenciamento de dependências e automação de builds.

### 3.3. Banco de dados
- **PostgreSQL:** sistema gerenciador de banco de dados relacional.

### 3.4. Infraestrutura
- **Docker:** containerização das aplicações.
- **Docker Compose:** gerenciamento e orquestração dos containers.

*Todas as aplicações e serviços deverão funcionar consistentemente em diferentes máquinas e ambientes.*

---

## 4. Arquitetura e Organização do Código

O projeto deverá seguir uma arquitetura modular, organizada e de fácil manutenção.

### 4.1. Princípios gerais
- Aplicar o princípio da responsabilidade única (SRP).
- Separar responsabilidades entre as camadas.
- Evitar acoplamento desnecessário.
- Separar regras de negócio, infraestrutura e apresentação.
- Priorizar composição em vez de herança desnecessária.
- Evitar duplicação de código (DRY).
- Aplicar os princípios SOLID quando pertinentes.
- Manter cada módulo responsável por funcionalidades bem definidas.

### 4.2. Semântica e nomenclatura
Todas as estruturas de código deverão ser semânticas, deixando evidente sua finalidade e responsabilidade.

**Evitar:**
- Nomes genéricos quando houver alternativas mais descritivas.
- Abreviações que dificultem a compreensão.
- Métodos com múltiplas responsabilidades.
- Classes com responsabilidades distintas.
- Componentes excessivamente grandes.
- Estruturas desnecessariamente complexas.

**Exemplo correto:**

```java
public BigDecimal calculateOrderTotal(Order order) {
    // Calcula o valor total do pedido
}
```

**Exemplo incorreto:**

```java
public BigDecimal calc(Order o) {
    // Calcula o pedido
}
```

---

## 5. Regras de Desenvolvimento Frontend

O desenvolvimento frontend deverá seguir as seguintes regras:
- Utilizar React com JavaScript (ES6+).
- Não utilizar TypeScript ou arquivos com extensão `.ts` e `.tsx`.
- Utilizar componentes funcionais do React.
- Utilizar React Hooks adequadamente.
- Criar componentes reutilizáveis.
- Manter cada componente com uma responsabilidade bem definida.
- Separar a lógica de negócio da apresentação visual quando apropriado.
- Utilizar elementos HTML semanticamente corretos.
- Considerar acessibilidade (a11y).
- Evitar renderizações desnecessárias.
- Organizar chamadas à API em serviços ou módulos específicos.
- Utilizar módulos JavaScript com `import` e `export`.
- Evitar concentrar toda a aplicação em um único componente.
- Manter uma estrutura de pastas organizada e padronizada.
- Utilizar nomes de componentes, funções e variáveis em inglês.
- Escrever comentários no código em português brasileiro.

---

## 6. Regras de Desenvolvimento Backend

O desenvolvimento backend deverá seguir as seguintes regras:
- Utilizar Java 21.
- Seguir as convenções do Spring Boot.
- Organizar o código em camadas arquiteturais.
- Utilizar injeção de dependências do Spring.
- Utilizar DTOs para objetos de entrada e saída quando apropriado.
- Manter Controllers responsáveis pela comunicação HTTP.
- Concentrar regras de negócio na camada Service.
- Utilizar Repository para persistência de dados.
- Implementar tratamento centralizado de exceções.
- Validar dados recebidos pelas requisições.
- Utilizar códigos HTTP adequados.
- Evitar expor entidades do banco diretamente nas APIs públicas.

### 6.1. Estrutura sugerida de pacotes

```text
com.project
├── config
├── controller
├── dto
├── entity
├── exception
├── mapper
├── repository
├── service
└── ProjectApplication.java
```

---

## 7. Regras de Banco de Dados

Ao trabalhar com PostgreSQL, o agente deverá:
- Utilizar modelagem relacional adequada.
- Definir corretamente chaves primárias e estrangeiras.
- Aplicar restrições de integridade.
- Utilizar nomes semânticos para tabelas e colunas.
- Evitar duplicação desnecessária de informações.
- Criar índices quando necessário.
- Garantir a integridade dos dados.
- Utilizar migrations para controlar alterações na estrutura do banco.
- Nunca armazenar credenciais diretamente no código-fonte.

---

## 8. Docker e Configuração de Ambiente

O Docker deverá ser utilizado para garantir que a aplicação funcione consistentemente em diferentes máquinas.

O projeto deverá possuir:
- `Dockerfile` para o frontend.
- `Dockerfile` para o backend.
- Arquivo `docker-compose.yml`.
- Configuração do container PostgreSQL.
- Gerenciamento de variáveis de ambiente.

**Regras obrigatórias:**
- Nunca inserir credenciais diretamente nos arquivos de código.
- Utilizar variáveis de ambiente para configurações específicas de cada ambiente.
- Disponibilizar um arquivo `.env.example`.
- Configurar corretamente as dependências entre serviços.
- Utilizar volumes persistentes para os dados do banco.
- Garantir que a aplicação possa ser iniciada utilizando Docker Compose.
- Documentar os comandos necessários para iniciar e encerrar o ambiente.

---

## 9. Qualidade de Código

Todas as implementações deverão priorizar:
- Legibilidade.
- Manutenibilidade.
- Reutilização.
- Escalabilidade.
- Segurança.
- Desempenho.

**Regras adicionais:**
- Evitar comentários desnecessários.
- Escrever comentários somente quando ajudarem a explicar comportamentos complexos ou não evidentes.
- Escrever todos os comentários em português brasileiro.
- Evitar números mágicos e valores literais sem explicação.
- Tratar erros explicitamente.
- Evitar blocos de tratamento de exceções vazios.
- Remover imports e variáveis não utilizados.
- Não deixar instruções de depuração desnecessárias.
- Não duplicar funcionalidades existentes.

---

## 10. Segurança

A segurança deverá ser considerada durante todas as etapas do desenvolvimento.

O agente **DEVE**:
- Validar e sanitizar entradas externas.
- Proteger informações sensíveis.
- Nunca expor senhas, tokens ou credenciais.
- Utilizar práticas seguras de autenticação e autorização quando necessário.
- Evitar vulnerabilidades de SQL Injection.
- Configurar CORS adequadamente.
- Evitar expor detalhes internos da implementação nas respostas de erro das APIs.

---

## 11. Testes Automatizados

Sempre que uma funcionalidade for implementada ou modificada:
- Criar ou atualizar os testes relacionados.
- Testar regras de negócio independentemente.
- Validar o comportamento das APIs.
- Testar componentes frontend quando apropriado.
- Garantir que os testes existentes continuem funcionando.
- Nunca remover testes simplesmente para fazer a compilação passar.

---

## 12. Git e Gerenciamento do Projeto

- Utilizar mensagens de commit descritivas em inglês.
- Manter alterações focadas na tarefa solicitada.
- Não sobrescrever implementações existentes sem compreender sua finalidade.
- Nunca versionar credenciais ou arquivos sensíveis.
- Manter o `.gitignore` atualizado.

---

## 13. Fluxo de Trabalho Obrigatório do Agente de IA

Antes de implementar qualquer tarefa, o agente **DEVERÁ** seguir esta sequência:

1. Ler integralmente este arquivo `AGENTS.md`.
2. Analisar a estrutura atual do projeto.
3. Compreender as implementações existentes.
4. Identificar os arquivos e componentes que precisarão ser criados ou modificados.
5. Planejar a implementação.
6. Verificar se a solução proposta respeita as regras e a arquitetura do projeto.
7. Implementar a funcionalidade solicitada.
8. Executar os testes e validações pertinentes.
9. Revisar as alterações realizadas, verificando qualidade e consistência.
10. Apresentar ao usuário um resumo da implementação, explicando as decisões técnicas em português brasileiro.

---

## 14. Regra Final

O agente de IA deverá priorizar a consistência, qualidade e manutenibilidade do projeto em vez da velocidade de implementação.

Nenhuma implementação deverá desrespeitar as regras estabelecidas neste documento sem antes informar o usuário e obter sua aprovação quando necessário.

*Este documento deverá ser considerado a principal referência de desenvolvimento durante todo o ciclo de vida do projeto.*