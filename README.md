# 🌟 🐍 Detecção de Flares Estelares com Python e TESS

Este projeto tem como objetivo detectar **flares e super-flares** em estrelas utilizando dados do telescópio espacial **TESS**. Flares são explosões súbitas na superfície estelar que liberam grandes quantidades de energia. Estudar esses fenômenos ajuda a entender a **atividade magnética das estrelas** e seus impactos em planetas ao redor.

---

## Funcionalidades do Programa
- Baixa e processa curvas de luz de estrelas do **TESS Input Catalog (TIC)**.  
- Detecta **flares e super-flares**, identificando eventos de alta intensidade.  
- Conta o número de flares por estrela.  
- Mapeia estrelas mais ativas em catálogos específicos.  
- Calcula métricas como intensidade máxima, duração e energia dos eventos.  

---

## Como Funciona a Detecção de Flares

O algoritmo de detecção segue os seguintes passos:

1. **Pré-processamento da curva de luz:**  
   - As curvas de luz do TESS são unidas e normalizadas.  
   - Valores faltantes (NaNs) são removidos para evitar falsos positivos.  
   - Filtragem de tendência de longo prazo usando suavização ou splines para destacar variações rápidas.

2. **Identificação de picos:**  
   - O fluxo normalizado é analisado para encontrar aumentos súbitos acima de um **limiar estatístico**, geralmente definido como `n` vezes o desvio padrão do fluxo.  
   - Cada pico que excede esse limiar é marcado como um candidato a flare.

3. **Caracterização do evento:**  
   - Para cada candidato, o algoritmo determina:  
     - **Intensidade máxima:** o pico de fluxo durante o flare.  
     - **Duração:** intervalo de tempo em que o fluxo permanece acima do limiar.  
     - **Energia aproximada:** integral do fluxo durante o evento.  

4. **Filtragem de falsos positivos:**  
   - Picos muito curtos ou fora dos parâmetros esperados são descartados.  
   - Eventos consecutivos próximos podem ser combinados, se fizer sentido fisicamente.  

5. **Super-flares:**  
   - Eventos com intensidade muito superior ao normal são classificados como super-flares, permitindo estudo de extremos da física estelar.

---

## Tecnologias Utilizadas
- Python  
- [Lightkurve](https://docs.lightkurve.org/) para manipulação de curvas de luz do TESS  
- Pandas e Numpy para análise de séries temporais  
- Matplotlib/Seaborn para visualização de resultados  

---

## Como Usar
1. Instale as dependências listadas no `requirements.txt`.  
2. Execute o script principal fornecendo o **TIC** das estrelas que deseja analisar.  
3. O programa gera:  
   - Gráficos de curvas de luz com flares destacados.  
   - Arquivos CSV com métricas de cada flare detectado.  

---

## Contribuição
Contribuições são bem-vindas! Abra **issues** ou envie **pull requests**.  

---

## Sobre
O estudo de flares estelares é fundamental para a astrofísica, pois flares intensos podem afetar a **habitabilidade de planetas** e fornecer insights sobre **extremos da física estelar**.

