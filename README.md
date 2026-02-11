# Análise Automatizada de Pull Requests

Aluno: Fernando da Silva Jordão
RA: 2501630

---

## Objetivo do Trabalho

Demonstrar domínio de Prompt Engineering por meio da criação evolutiva de três versões (v1, v2 e v3) de um prompt para análise automatizada de Pull Requests de Infraestrutura como Código (IaC).

Cada versão representa uma melhoria em relação à anterior, buscando maior controle, padronização e segurança na saída gerada pelo modelo.

---

## Raciocínio Utilizado na Criação dos Prompts

### 🔹 v1 – Baseline

A primeira versão foi criada de forma simples e direta, com instruções abertas para análise de:

- Segurança
- Custo
- Compliance
- Boas práticas

O objetivo foi estabelecer um ponto inicial de comparação.  
Essa versão permite maior liberdade ao modelo, mas apresenta:

- Alta variabilidade de resposta
- Falta de padronização
- Dificuldade de automação

Ela representa um prompt funcional, porém pouco controlado.

---

### 🔹 v2 – Structured

A segunda versão foi criada para resolver os problemas da v1.

Melhorias aplicadas:

- Estrutura obrigatória de resposta
- Campos fixos (Severidade, Decisão, Categoria, Descrição, Ações)
- Proibição de seções extras

O objetivo foi aumentar a previsibilidade da saída e reduzir variações no formato.

Essa versão já é mais adequada para uso operacional, porém ainda não possui mecanismos explícitos contra prompt injection.

---

### 🔹 v3 – Schema + Segurança

A terceira versão foi projetada para ser a mais robusta e consistente.

Melhorias implementadas:

- Resposta exclusivamente em JSON válido
- Schema fixo e determinístico
- Proibição de texto fora do JSON
- Regras explícitas para ignorar instruções contidas no PR

O principal avanço foi a inclusão de proteção contra prompt injection, garantindo que:

- O PR seja tratado apenas como dado
- Instruções maliciosas no código não alterem o comportamento do modelo

Essa versão é a mais adequada para integração em pipelines automatizados de CI/CD.

---

## Conclusão

A evolução v1 → v2 → v3 demonstra:

- Aumento progressivo de controle
- Maior padronização da saída
- Melhor adequação para automação
- Inclusão de segurança contra manipulação do modelo

A versão v3 apresenta os resultados mais consistentes e previsíveis entre todas as versões.
