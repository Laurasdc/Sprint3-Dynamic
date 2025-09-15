# Projeto: Controle de Estoque com Estruturas de Dados Clássicas

![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)

## 1. Visão Geral do Projeto

Este projeto foi desenvolvido para a disciplina de **Programação Dinâmica** e aborda um desafio prático em unidades de diagnóstico: a gestão ineficiente do consumo diário de insumos (reagentes e descartáveis). A ausência de um registro preciso dificulta o controle de estoque, a prevenção de perdas por validade e a previsão de reposição.

A solução proposta utiliza estruturas de dados e algoritmos clássicos para simular o registro de consumo, organizar os dados e permitir análises estratégicas, transformando dados brutos em informação valiosa para a tomada de decisão.

## 2. Tecnologias Utilizadas

* **Linguagem:** Python 3
* **Ambiente:** Jupyter Notebook
* **Bibliotecas:** `collections.deque` para implementação de Fila.

## 3. Como Executar

Para visualizar e executar a simulação, siga os passos abaixo:

1.  **Clone o Repositório:**
    ```bash
    git clone [https://github.com/seu-usuario/nome-do-repositorio.git](https://github.com/seu-usuario/nome-do-repositorio.git)
    ```
2.  **Navegue até a Pasta:**
    ```bash
    cd nome-do-repositorio
    ```
3.  **Abra o Jupyter Notebook:** Certifique-se de que você tem o Jupyter instalado. Se não, instale-o com `pip install notebook`. Em seguida, inicie o ambiente:
    ```bash
    jupyter notebook
    ```
4.  **Execute o Projeto:** Na interface do Jupyter que abrirá no seu navegador, clique no arquivo `.ipynb` do projeto. Uma vez aberto, execute as células de código em ordem sequencial para ver a simulação e os relatórios gerados.

## 4. Análise das Estruturas e Algoritmos (Relatório)

Esta seção detalha como cada estrutura de dados e algoritmo foi aplicado para resolver partes específicas do problema de gerenciamento de insumos.

### 4.1. Fila e Pilha

#### **Fila (Queue)**

* **Aplicação:** A Fila foi a escolha ideal para registrar o consumo diário. Sua natureza **FIFO (First-In, First-Out)** garante que os insumos sejam processados na mesma ordem em que foram consumidos.
* **Contexto do Problema:** Em um sistema real, isso é crucial para manter a integridade cronológica dos dados, alimentar logs de auditoria e integrar com sistemas de baixa de estoque em tempo real. A implementação usou a classe `deque` por sua alta performance em operações de adição (`append`) e remoção (`popleft`).

#### **Pilha (Stack)**

* **Aplicação:** A Pilha foi utilizada para simular consultas em ordem inversa, acessando os últimos consumos primeiro, graças à sua característica **LIFO (Last-In, First-Out)**.
* **Contexto do Problema:** Esta estrutura é perfeita para funcionalidades que demandam acesso rápido ao dado mais recente, como um painel de "últimas atividades", ou para implementar uma função de "desfazer" (undo) um registro de consumo feito por engano.

### 4.2. Estruturas de Busca

#### **Busca Sequencial**

* **Aplicação:** Implementada para localizar todos os registros de consumo de um insumo específico. O algoritmo percorre a lista do início ao fim.
* **Contexto do Problema:** Embora simples, é uma ferramenta útil para buscas em conjuntos de dados pequenos ou quando os dados não estão ordenados, permitindo auditorias rápidas sobre o histórico de uso de um item.

#### **Busca Binária**

* **Aplicação:** Demonstra uma busca de altíssima eficiência para encontrar um insumo em uma lista **previamente ordenada** por nome.
* **Contexto do Problema:** Em um banco de dados com milhares de registros de consumo, a busca binária (complexidade `O(log n)`) é drasticamente mais rápida que a sequencial (`O(n)`), tornando as consultas ao sistema praticamente instantâneas e garantindo uma boa experiência ao usuário.

### 4.3. Algoritmos de Ordenação

#### **Merge Sort**

* **Aplicação:** Utilizado para ordenar os insumos por **quantidade consumida**, permitindo a rápida identificação dos itens de maior ou menor giro.
* **Contexto do Problema:** Escolhemos o Merge Sort por sua performance estável e previsível (`O(n log n)` em todos os cenários). Gerar um relatório dos itens mais consumidos é fundamental para o setor de compras planejar a reposição de estoque de forma proativa.

#### **Quick Sort**

* **Aplicação:** Empregado para ordenar os insumos pela **data de validade**.
* **Contexto do Problema:** Essa ordenação é a base da estratégia **FEFO (First-Expire, First-Out)**, crucial para minimizar perdas financeiras. Ao saber quais lotes de insumos estão mais próximos do vencimento, a gestão pode priorizar seu uso, evitando desperdício.

### 4.4. Otimização com Tabela Hash

* **Aplicação:** Para consolidar o consumo total por tipo de insumo, utilizamos um dicionário do Python, que é uma implementação de Tabela Hash.
* **Contexto do Problema:** Em vez de percorrer a lista várias vezes para calcular o total de cada item, a Tabela Hash permite agregar todos os valores em uma única passada (`O(n)`), com buscas e inserções em tempo médio constante (`O(1)`). Isso torna a geração de relatórios de resumo extremamente rápida e eficiente.
