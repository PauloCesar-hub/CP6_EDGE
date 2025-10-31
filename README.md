# 🌱 Projeto IoT - Monitoramento de Planta com ESP32, DHT22 e LDR

Este projeto tem como objetivo monitorar **temperatura, umidade e luminosidade** de uma planta utilizando o **ESP32**, enviando os dados via **MQTT (HiveMQ)** e visualizando tudo em tempo real no **Node-RED Dashboard**.

---

## 🚀 Visão Geral

O sistema coleta dados de sensores (DHT22 e LDR) e publica em um broker MQTT.  
O Node-RED consome esses dados e exibe em um **dashboard interativo**, permitindo acompanhamento em tempo real.

📡 **Tecnologias utilizadas:**
- ESP32 (Arduino IDE)
- DHT22 (Sensor de temperatura e umidade)
- LDR (Sensor de luminosidade)
- Wi-Fi
- MQTT (via broker público HiveMQ)
- Node-RED + Dashboard UI

---

🔗 Links Importantes
Descrição	Link
🌍 Broker MQTT público utilizado	broker.hivemq.com
💡 Simulador Wokwi (https://wokwi.com/projects/446291445837477889)	Simular no Wokwi

📡 Conexões do Circuito
text
Copiar código
ESP32
│
├── D4  →  DHT22 (pino de dados)
├── D35 →  LDR (via divisor de tensão)
├── D2  →  LED indicador
└── 3V3 e GND → Alimentação dos sensores
💡 Dica: se estiver simulando no Wokwi, conecte o LDR entre 3V3 e o pino A2 (com resistor de 10kΩ para o GND).
---
<div align="center">
  <img src="tela" width="600" alt="Arquitetura do Projeto">
</div>

🧠 Como Funciona
O ESP32 conecta-se ao Wi-Fi.

Lê os valores dos sensores (DHT22 e LDR).

Publica os dados nos tópicos MQTT:

planta/temperatura

planta/umidade

planta/luminosidade

O Node-RED recebe os dados e exibe no dashboard.
---
🧰 Passos para Reproduzir o Projeto
🔹 1. Configurar o ESP32
Instale a Arduino IDE e adicione o suporte ao ESP32.

Baixe o código do ESP32 no link acima.

Instale as bibliotecas:

PubSubClient

DHT sensor library

Conecte o ESP32 e envie o código.

🔹 2. Configurar o Node-RED
Instale o Node-RED:

bash
Copiar código
npm install -g --unsafe-perm node-red
node-red
Acesse o painel: http://localhost:1880

Vá em Menu → Import → Clipboard

Cole o JSON do fluxo (link acima)

Clique em Deploy

Abra o Dashboard: http://localhost:1880/ui

📊 Dashboard Node-RED
O dashboard mostra em tempo real:

Sensor	Tipo	Unidade	Exemplo
Temperatura	Gauge + Gráfico	°C	26.5
Umidade	Gauge + Gráfico	%	55
Luminosidade	Gauge + Indicador de LED	%	80
---
🧾 Tópicos MQTT Utilizados
Tópico	Tipo de Dado	Exemplo
planta/temperatura	Float	26.5
planta/umidade	Float	54.2
planta/luminosidade	Int (0–100)	78
---
🛠️ Solução de Problemas
Erro	Possível Solução
Temperatura/Umidade retornando NaN	Verifique o pino e tipo do DHT (DHT22 ou DHT11)
Luminosidade sempre 0	Confirme o resistor de 10kΩ e se o LDR está ligado corretamente
Sem dados no dashboard	Confira se o Node-RED está conectado ao broker MQTT
---
👨‍💻 Autores
- Paulo Cesar de Govea Junior - (RM:566034)
- Guilherme Vilela Perez - (RM:564422)
- Gustavo Panham Dourado - (RM:563904)
- Christian Schunck de Almeida - (RM:563850)
- Thomas Jeferson Santana Wang - (RM565104)
  
💬 Projeto desenvolvido para aprendizado em IoT e Edge Computing


🪴 Licença
Este projeto é de uso educacional e livre para modificações.
Atribuição é bem-vinda 🌱
