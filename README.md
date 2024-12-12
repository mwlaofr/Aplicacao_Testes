# Testes de Desempenho com JMeter no Site do Portfólio

## Introdução
Este documento descreve o processo de aplicação de testes de desempenho no site do meu portfólio hospedado no GitHub Pages utilizando o Apache JMeter. O objetivo é verificar o comportamento do site sob diferentes cargas de usuários simulados, analisando o tempo de resposta e a estabilidade do serviço.

---

## O que foi feito
1. **Configuração Inicial:**
   - Foi criado um Test Plan no JMeter contendo um *Thread Group* para simular usuários.
   - Adicionou-se um sampler HTTP Request apontando para o URL do site do portfólio.

2. **Testes Implementados:**
   - Primeiro teste: 10 usuários, iniciando em 5 segundos, repetindo 5 vezes.
   - Segundo teste: Aumento gradual de usuários até 1.000, iniciando em 10 segundos, repetindo 50 vezes.

3. **Coleta de Resultados:**
   - Utilização de *Listeners* como View Results Tree e Summary Report para coletar e analisar os resultados das requisições.

4. **Validação de Erros:**
   - No teste com 1.000 usuários, foram observados erros HTTP 429 (Too Many Requests), indicando um limite do servidor para lidar com altas cargas simultâneas.
   - Apesar dos erros, o site manteve-se operacional quando acessado diretamente.

---

## Como executar
1. **Instalação do JMeter:**
   - Baixe e instale o Apache JMeter no site oficial: https://jmeter.apache.org/.

2. **Configuração do Test Plan:**
   - Abra o JMeter e crie um novo Test Plan.
   - Adicione um Thread Group:
     - Configure o número de usuários (Threads) e o tempo de ramp-up (tempo para iniciar todos os usuários).
     - Defina o número de repetições (Loops).
   - Adicione um HTTP Request Sampler:
     - Insira o URL do site do portfólio.
   - Adicione os Listeners:
     - *View Results Tree* para visualizar as requisições e respostas.
     - *Summary Report* para analisar os tempos de resposta e vazão.

3. **Execução dos Testes:**
   - Execute o Test Plan clicando no botão de play.
   - Monitore os resultados nos Listeners configurados.

---

## Testes Implementados
### Teste 1: 10 Usuários
- **Configuração:**
  - 10 threads
  - 5 segundos de ramp-up
  - 5 repetições
- **Resultados:**
  - Todas as requisições retornaram códigos HTTP 200 (sucesso).
  - Relatório resumido apresentou:
    - Tempo mínimo, máximo e médio de resposta.
    - Vazão (requests/segundo) e consumo de banda (KB/segundo).

### Teste 2: 1.000 Usuários
- **Configuração:**
  - 1.000 threads
  - 10 segundos de ramp-up
  - 50 repetições
- **Resultados:**
  - Muitos erros HTTP 429, indicando que o servidor atingiu o limite de requisições simultâneas.
  - Apesar dos erros, o site permaneceu funcional e responsivo quando acessado diretamente pelo navegador.

---

## Conclusão
Os testes demonstraram que o site do portfólio é capaz de lidar com cargas moderadas de usuários simultâneos. No entanto, ao simular 1.000 usuários, o servidor apresentou limitações, retornando erros HTTP 429. Mesmo assim, o site manteve sua operação sem quedas ou instabilidades.

O JMeter se mostrou uma ferramenta eficiente para testes de desempenho, permitindo a análise detalhada do comportamento do site sob diferentes condições de carga.

### Autoras
- **Millena França**
- **Melina Nogueira**

