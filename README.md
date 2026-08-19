# AQUA-SENSE — Sistema Embarcado de Monitoramento Óptico de Efluentes

### Monitoramento Óptico em Linha para Análise de Efluentes com Eletrônica Embarcada

## Status

🔵 **Pesquisa / P&D — Etapa conceitual**

O projeto encontra-se atualmente em **fase de pesquisa e desenvolvimento conceitual**, fundamentado em estudos bibliográficos, definição de arquitetura experimental e resultados de pesquisa acadêmica previamente publicados.

**A implementação prática do sistema embarcado, incluindo desenvolvimento do hardware, firmware, sistema óptico, calibração experimental e operação em linha, será desenvolvida futuramente.**

---

## Sobre o Projeto

O **AQUA-SENSE** é uma proposta de sistema embarcado para **monitoramento óptico em linha de efluentes líquidos**, utilizando uma fonte luminosa, sensor óptico e microcontrolador para estimar características relacionadas à absorção e transmissão da luz através do fluido.

A proposta surgiu a partir de uma pesquisa de iniciação científica voltada ao **aproveitamento de resíduos da construção civil como materiais adsorventes para remoção de corantes de efluentes de indústrias têxteis**.

A pesquisa investigou o uso de resíduos cerâmicos, especialmente tijolos e pisos, como adsorventes. Os experimentos demonstraram resultados promissores para o uso de cerâmica vermelha, com destaque para granulometrias menores.

Paralelamente, foi proposta a utilização de um sistema óptico associado a um microcontrolador para realizar medições **em linha**, reduzindo a dependência de coleta de amostras para análise convencional.

---

# Objetivo

Desenvolver futuramente um sistema eletrônico embarcado capaz de realizar **monitoramento óptico contínuo de efluentes**, utilizando aquisição de sinais de um sensor óptico, processamento embarcado e calibração baseada em equipamentos analíticos de referência.

A proposta contempla:

* aquisição do sinal óptico;
* condicionamento eletrônico;
* conversão analógico-digital;
* processamento do sinal;
* cálculo de parâmetros ópticos;
* calibração experimental;
* monitoramento em linha;
* armazenamento e transmissão dos dados;
* possibilidade de integração com sistemas IoT.

---

# Contexto Científico

A pesquisa original avaliou resíduos de construção civil, especialmente **cerâmica vermelha e pisos**, como materiais adsorventes para remoção de corantes presentes em efluentes têxteis.

Os experimentos utilizaram diferentes granulometrias e concentrações de corante. A granulometria fina apresentou melhor resultado visual de adsorção, sendo posteriormente utilizada nos experimentos de concentração.

Os resultados publicados indicaram potencial para utilização da cerâmica vermelha como material adsorvente, embora também tenham apontado a necessidade de estudos futuros utilizando **métodos analíticos e operação em regime contínuo**.

O AQUA-SENSE representa uma evolução conceitual dessa linha de pesquisa, adicionando uma camada de **instrumentação eletrônica, aquisição de dados e monitoramento em linha**.

---

# Arquitetura Conceitual

```text
                  EFLUENTE
                     │
                     ▼
             ┌─────────────────┐
             │ Câmara de Fluxo │
             │                 │
             │ Fonte Óptica    │
             │       │         │
             │       ▼         │
             │    FLUIDO       │
             │       │         │
             │       ▼         │
             │ Sensor Óptico   │
             └────────┬────────┘
                      │
                      ▼
              Condicionamento
                 do Sinal
                      │
                      ▼
             Conversão ADC
                      │
                      ▼
             ┌────────────────┐
             │ Microcontrolador│
             │                │
             │ Processamento  │
             │ Filtragem      │
             │ Calibração     │
             │ Estimativa     │
             └───────┬────────┘
                     │
          ┌──────────┼──────────┐
          ▼          ▼          ▼
       Display     Serial      IoT
                              │
                              ▼
                       Banco / Dashboard
```

---

# Princípio de Funcionamento

A proposta utiliza uma fonte luminosa posicionada de forma que a radiação atravesse o efluente antes de atingir um elemento sensor.

A intensidade detectada pelo sensor será relacionada à intensidade de referência obtida sem a presença do fluido ou em condições controladas.

Conceitualmente:

```text
Fonte luminosa
      ↓
   I₀
      ↓
   Efluente
      ↓
    I
      ↓
Sensor óptico
      ↓
Microcontrolador
```

A partir das intensidades medidas, poderão ser calculadas grandezas ópticas como transmitância e absorbância:

[
T = \frac{I}{I_0}
]

[
A = -\log_{10}(T)
]

A relação entre a resposta óptica e a concentração do contaminante deverá ser determinada experimentalmente durante a futura etapa de validação.

---

# Desenvolvimento Proposto

O desenvolvimento prático está planejado em etapas.

## 1. Sistema Óptico

Desenvolvimento da câmara de medição contendo:

* fonte luminosa;
* caminho óptico controlado;
* sensor óptico;
* isolamento contra luz ambiente;
* entrada e saída de fluido.

A proposta original também considerava a utilização de material transparente adequado à região espectral utilizada, incluindo quartzo para minimizar interferências ópticas na região UV.

---

## 2. Eletrônica de Aquisição

Desenvolvimento de uma cadeia de aquisição composta por:

```text
Sensor
  ↓
Amplificador / Condicionamento
  ↓
Filtro
  ↓
ADC
  ↓
Microcontrolador
```

Serão avaliados futuramente:

* faixa dinâmica;
* resolução;
* ruído;
* frequência de amostragem;
* estabilidade;
* linearidade;
* saturação;
* repetibilidade das medições;
* resposta temporal.

---

## 3. Firmware

O firmware será responsável por:

* aquisição do ADC;
* filtragem digital;
* processamento dos sinais;
* compensação de baseline;
* cálculo das grandezas ópticas;
* aplicação da calibração;
* diagnóstico do sistema;
* armazenamento das medições;
* comunicação com sistemas externos.

---

## 4. Calibração

A calibração experimental será realizada utilizando soluções de concentração conhecida e um equipamento analítico de referência.

A pesquisa original propôs explicitamente que o microcontrolador fosse aferido utilizando um **espectrofotômetro previamente calibrado**.

A metodologia futura poderá seguir uma estrutura semelhante a:

```text
Solução de referência
        │
        ├───────────────┐
        ▼               ▼
Espectrofotômetro   AQUA-SENSE
        │               │
        ▼               ▼
Valor referência    Valor óptico
        │               │
        └───────┬───────┘
                ▼
       Modelo de calibração
```

---

# Pesquisa Experimental Futura

A implementação prática ainda **não foi realizada**.

A próxima fase deverá contemplar:

* construção do protótipo eletrônico;
* desenvolvimento da câmara óptica;
* seleção dos sensores;
* desenvolvimento do firmware;
* caracterização do sistema;
* preparação das soluções de referência;
* calibração;
* comparação com espectrofotometria;
* testes com diferentes concentrações;
* testes de estabilidade;
* testes em fluxo contínuo;
* avaliação da aplicação em monitoramento de efluentes.

Portanto, os resultados experimentais dessa etapa **não fazem parte do estado atual do projeto** e serão incorporados somente após sua execução e validação.

---

# Estado Atual

Atualmente, o AQUA-SENSE possui:

* fundamentação científica;
* pesquisa bibliográfica;
* definição conceitual do sistema;
* proposta de arquitetura de medição;
* definição preliminar do princípio óptico;
* proposta de utilização de microcontrolador;
* proposta de calibração com equipamento de referência;
* resultados de pesquisa acadêmica relacionados à adsorção;
* artigo científico publicado relacionado à linha de pesquisa.

A parte prática de instrumentação permanece como **desenvolvimento futuro**.

---

# O que este projeto demonstra

O projeto reúne conhecimentos relacionados a:

* Engenharia Elétrica;
* eletrônica embarcada;
* instrumentação;
* sensores;
* aquisição de sinais;
* ADC;
* processamento digital de sinais;
* sistemas ópticos;
* microcontroladores;
* firmware;
* calibração experimental;
* análise de dados;
* IoT;
* monitoramento ambiental;
* tratamento de efluentes;
* pesquisa aplicada.

---

# Relação com a Pesquisa Publicada

A pesquisa que originou o projeto avaliou resíduos cerâmicos provenientes da construção civil como adsorventes para remoção de corantes de efluentes têxteis.

O trabalho experimental utilizou resíduos de tijolos e pisos, submetidos a trituração e separação granulométrica, com avaliação de diferentes concentrações de corante.

Os resultados indicaram melhor desempenho para o resíduo de tijolo e para a granulometria fina.

A etapa de instrumentação proposta pelo AQUA-SENSE busca futuramente complementar essa linha de pesquisa através da substituição de avaliações predominantemente laboratoriais por um sistema de **aquisição e monitoramento óptico em linha**.

---

# Roadmap

## Fase 1 — Pesquisa

* [x] Levantamento bibliográfico
* [x] Definição do problema
* [x] Estudo do princípio de medição
* [x] Publicação da pesquisa relacionada
* [x] Definição conceitual da arquitetura

## Fase 2 — Projeto

* [ ] Especificação do sistema óptico
* [ ] Seleção do sensor
* [ ] Seleção do microcontrolador
* [ ] Projeto do condicionamento analógico
* [ ] Projeto da câmara de medição
* [ ] Definição do protocolo de comunicação

## Fase 3 — Desenvolvimento

* [ ] Construção do protótipo eletrônico
* [ ] Desenvolvimento do firmware
* [ ] Implementação da aquisição ADC
* [ ] Implementação do processamento digital
* [ ] Desenvolvimento da interface de monitoramento

## Fase 4 — Validação

* [ ] Calibração com soluções conhecidas
* [ ] Comparação com espectrofotômetro
* [ ] Avaliação de linearidade
* [ ] Avaliação de erro
* [ ] Avaliação de estabilidade
* [ ] Testes em regime contínuo

## Fase 5 — IoT

* [ ] Transmissão dos dados
* [ ] Armazenamento em banco de dados
* [ ] Dashboard
* [ ] Monitoramento remoto
* [ ] Alertas
* [ ] Avaliação de operação contínua

---

# Limitações Atuais

* O sistema embarcado ainda não foi construído.
* A arquitetura apresentada é conceitual.
* Os parâmetros ópticos ainda não foram caracterizados experimentalmente no novo sistema.
* A calibração ainda não foi realizada.
* Não existem métricas experimentais do AQUA-SENSE neste estágio.
* A relação entre resposta óptica e concentração ainda deverá ser determinada experimentalmente.
* A operação contínua ainda não foi implementada.
* A integração IoT permanece como evolução futura.

---

# Referência da Pesquisa

**SOUZA, B. C. R.; DUBBERN, Y. F.; RIBEIRO, B. M. B.**

**Aproveitamento de Resíduos da Construção Civil para Adsorção de Corantes de Indústrias Têxteis.**

O trabalho foi desenvolvido no contexto de iniciação científica, incluindo participação na área de Engenharia Elétrica, e investigou a utilização de resíduos cerâmicos como adsorventes para remoção de corantes de efluentes têxteis.

---

# Autor

**Yuri Fernando Dubbern**

Engenharia Elétrica · Ciência da Computação · IA · Sistemas Embarcados · Pesquisa e Desenvolvimento

[LinkedIn](https://www.linkedin.com/in/yuridubbern) · [GitHub](https://github.com/Yuri-Fernando)

---

> **AQUA-SENSE é um projeto de pesquisa aplicada em instrumentação, eletrônica embarcada e monitoramento ambiental, atualmente em etapa conceitual, com desenvolvimento experimental planejado para etapas futuras.**
