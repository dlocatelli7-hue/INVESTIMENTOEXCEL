# Simulador de Investimentos em Fundos Imobiliários (FIIs) 📈

Ferramenta desenvolvida em Excel com interface amigável ("cara de aplicativo") para simulação de aportes mensais, acumulação de patrimônio e projeção de dividendos em Fundos Imobiliários.

## 🎯 Perguntas de Negócio Respondidas
A ferramenta foi projetada para responder de forma clara a 5 perguntas essenciais para o investidor:
1. **Quanto investir por mês?** (Configurado através do aporte mensal ou sugestão percentual sobre o salário).
2. **Por quantos anos?** (Definido no horizonte de tempo da simulação).
3. **Qual a taxa de rendimento mensal?** (Rentabilidade estimada da carteira ao mês).
4. **Quanto de patrimônio vai acumular?** (Calculado automaticamente através da função financeira `VF`).
5. **Quanto vai receber de dividendos por mês?** (Derivado do patrimônio acumulado multiplicado pela taxa).

As respostas aparecem diretamente no painel principal de resumo e na tabela dinâmica de projeções de 2 a 30 anos.

---

## ⚙️ Como a Lógica Funciona por Dentro

### 1. Função VF (Valor Futuro)
A função `VF` calcula o montante acumulado ao longo do tempo considerando depósitos (aportes) regulares e uma taxa de juros composta constante por período. Na planilha, ela cruza o prazo em meses (anos $\times$ 12), a taxa de rendimento mensal e o valor do aporte para projetar o patrimônio final.

### 2. Função PROCV com Chave Composta
Para dividir o patrimônio/aporte entre os diferentes tipos de FIIs de acordo com o perfil escolhido, foi utilizada uma **chave composta** (concatenando o *Perfil* e o *Tipo de Fundo*, ex: `Moderado-Papel`). Isso permite que o `PROCV` busque de forma única e exata o percentual correto na aba de apoio sem conflitos.

### 3. Intervalos Nomeados
Para tornar as fórmulas mais legíveis e fáceis de auditar, foram criados intervalos nomeados substituindo endereços fixos de células (como `$B$5`) por nomes intuitivos, a exemplo de:
* `aporte`
* `taxa_mensal`
* `prazo_anos`

---

## 📊 Perfis de Investidor e Distribuição de Aportes
A planilha conta com uma aba de apoio contendo a matriz de percentuais para cada perfil (Conservador, Moderado e Agressivo), garantindo que a soma de cada perfil atinja exatamente **100%**.

*(Dica: Insira aqui prints da sua planilha preenchida comparando dois perfis diferentes para evidenciar o funcionamento dinâmico da validação de dados e da divisão dos aportes).*

---

## 🚀 O que foi personalizado / Evoluções em relação à base do Expert
* Organização visual aprimorada do painel de controle principal.
* Ajustes nos rótulos e formatação condicional para simular a experiência de um software financeiro real.
