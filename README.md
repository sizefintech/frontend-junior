# 💻 Desafio Técnico — Frontend (React ou React Native)  
## Simulador de Antecipação de Recebíveis

### 🎯 Objetivo  
Desenvolver uma **aplicação frontend responsiva** que permita a uma empresa simular a antecipação de recebíveis com base em regras de negócio.  
Todos os dados podem ser armazenados **localmente (em memória ou localStorage)**, **sem necessidade de backend real**.

---

### 🧩 Funcionalidades Requeridas

#### 1. Cadastro de Empresa  
Criar um formulário com os seguintes campos:
- **CNPJ** (obrigatório, com máscara e validação básica)
- **Nome da Empresa** (obrigatório)
- **Faturamento Mensal** (obrigatório, input numérico)
- **Ramo** (obrigatório, opções: `"Serviços"` ou `"Produtos"`)

Após o cadastro, exibir os dados e o **limite de crédito calculado** com base nas regras:

| Faturamento Mensal      | Serviços              | Produtos              |
|-------------------------|------------------------|------------------------|
| R$ 10.000 a R$ 50.000   | 50% do faturamento     | 50% do faturamento     |
| R$ 50.001 a R$ 100.000  | 55% do faturamento     | 60% do faturamento     |
| Acima de R$ 100.000     | 60% do faturamento     | 65% do faturamento     |

---

#### 2. Cadastro de Notas Fiscais  
Permitir que a empresa cadastre múltiplas NFs com os campos:
- **Número da Nota** (obrigatório)
- **Valor Bruto** (obrigatório, numérico)
- **Data de Vencimento** (obrigatório, deve ser futura)

Exibir uma lista das notas cadastradas, com opção de remover.

---

#### 3. Carrinho de Antecipação  
Permitir ao usuário:
- Adicionar/remover NFs ao "Carrinho de Antecipação"
- O total bruto das NFs no carrinho **não pode ultrapassar o limite de crédito**

---

#### 4. Cálculo de Antecipação (Simulação)  
Exibir o valor **líquido** de cada NF e o **total líquido** do carrinho com base na fórmula:

- **Taxa**: 4,65% ao mês  
- **Prazo**: diferença entre a **data atual e a data de vencimento** (em dias)  
- **Deságio por nota**:  
  ```plaintext
  Deságio = ValorNF / (1 + 0.0465)^(Prazo / 30)
  Valor Líquido = ValorNF - Deságio
  ```

##### Exemplo de retorno esperado:

```json
{
  "empresa": "Nome da Empresa",
  "cnpj": "XXXXXXXXXXXXXX",
  "limite": 50000,
  "notas_fiscais": [
    {
      "numero": 1234,
      "valor_bruto": 10000,
      "valor_liquido": 9534.88
    }
  ],
  "total_bruto": 10000,
  "total_liquido": 9534.88
}
```

---

### 🧑‍💻 Requisitos Técnicos
- React.js (web) ou React Native (mobile)
- UI amigável, responsiva e intuitiva
- Utilizar **hooks** e **componentização**
- Armazenar dados em `useState`, `useReducer` ou `localStorage`
- Uso de biblioteca de UI (opcional)

---

### 📦 Entrega Esperada
- Código-fonte hospedado no GitHub ou ZIP
- Instruções no `README.md` explicando como rodar a aplicação
- Lista de melhorias ou ideias futuras
