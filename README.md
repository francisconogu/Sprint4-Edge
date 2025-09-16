Sistema de Análise de Jogo de Futebol (IoT)

💻 Integrantes

Bruna Sadi Duarte, rm: 561870

Bernardo Moreira, rm: 564103

Francisco Nogueira de Queiroz, rm:566309

Rhariel, rm: 566310

Sara Maragon, rm:563807

📝 Descrição do Projeto

Este projeto é um sistema de monitoramento de dados em tempo real para jogos de futebol, utilizando uma solução de Internet das Coisas (IoT). O objetivo principal é coletar, processar e visualizar informações cruciais sobre as condições ambientais e métricas de jogo, oferecendo uma análise detalhada do evento.

O sistema se concentra em três tipos principais de dados:

Condições Ambientais: Utilizando um sensor DHT22, o projeto monitora a temperatura e a umidade no campo. Essa informação é vital para avaliar o desempenho dos jogadores e as condições do ambiente de jogo.

Tempo de Posse de Bola: Através de etiquetas RFID acopladas à bola e aos jogadores, o sistema é capaz de identificar qual time está com a posse de bola. Isso permite calcular o tempo de posse de bola de cada equipe, uma métrica fundamental para a análise tática.

Distância Percorrida pela Bola: Um módulo RTK GPS integrado rastreia a distância total percorrida pela bola durante a partida. Esse dado oferece uma perspectiva sobre a dinâmica do jogo e a intensidade dos lances.

Todos os dados são coletados por um ESP32 e enviados para um servidor local. Em seguida, são processados e visualizados em uma plataforma intuitiva, proporcionando uma ferramenta poderosa para técnicos, analistas e entusiastas do esporte.

🏛️ Arquitetura Proposta

<img width="1469" height="807" alt="Diagrama" src="https://github.com/user-attachments/assets/fcaae9ab-1832-43ba-8ac2-d33f7806fc05" />

A arquitetura do projeto é baseada em um sistema de Internet das Coisas (IoT), focado na coleta e visualização de dados. O fluxo de informações segue as seguintes etapas:

Sensores e Módulo Central: O projeto utiliza diversos sensores para capturar dados do ambiente.

Um sensor DHT22 é responsável pela medição de temperatura e umidade.

Um módulo RTK GPS fornece dados de geolocalização de alta precisão.

Um leitor RFID é usado para identificação de objetos ou pessoas.

Todos esses sensores estão conectados a um microcontrolador ESP32, que atua como o cérebro do sistema, processando os dados e preparando-os para o próximo estágio.

Dispositivos IoT e Nuvem: O ESP32, agora considerado um Dispositivo IoT, envia os dados coletados para a nuvem. Essa comunicação é feita de forma eficiente e segura.

Broker MQTT: Os dados chegam a um Broker MQTT, que é um servidor que gerencia o fluxo de mensagens entre os dispositivos. Ele atua como um hub central, garantindo que as informações sejam encaminhadas corretamente para o software que as processará. O protocolo MQTT (Message Queuing Telemetry Transport) é ideal para IoT, pois é leve e otimizado para redes com baixa largura de banda.

Software Local (Node-RED): Um software local, rodando em um servidor com Node-RED, recebe as mensagens do Broker MQTT. O Node-RED é uma ferramenta de programação visual baseada em fluxos de eventos. Ele processa, armazena e manipula os dados conforme a necessidade do projeto, preparando-os para a visualização.

Plataforma de Visualização: Por fim, os dados processados pelo Node-RED são enviados para uma Plataforma de Visualização. Esta plataforma pode ser um painel de controle (dashboard) web, uma aplicação mobile ou outro tipo de interface que permite ao usuário final monitorar e analisar os dados coletados de forma intuitiva.

Essa arquitetura garante um fluxo de dados contínuo e confiável, desde a captura pelos sensores até a sua apresentação final ao usuário.

⚙️ Recursos Necessários

Wokwi: Para a simulação do hardware (ESP32, DHT22, RTK GPS e RFID). A plataforma Wokwi permite testar o código e a lógica dos sensores sem a necessidade de componentes físicos.

Servidor Node-RED: Para processar e visualizar os dados. O Node-RED é usado para criar os fluxos de mensagens que recebem os dados do MQTT Broker e os encaminham para a plataforma de visualização.

Broker MQTT: Um servidor MQTT, como o Mosquitto, para gerenciar a comunicação entre o dispositivo (ESP32) e o software (Node-RED).

Plataforma de Visualização: Um dashboard ou uma interface web para exibir os dados em tempo real. Você pode usar uma das muitas opções do próprio Node-RED ou integrar com outra ferramenta de visualização.

Bibliotecas de software:

Para o ESP32 (Wokwi): Bibliotecas específicas para os sensores DHT, GPS e RFID (por exemplo, DHT.h e PubSubClient).

Para o Node-RED: Nós (nodes) específicos para MQTT, armazenamento de dados e visualização (por exemplo, node-red-dashboard).

Hardware (se for usar na vida real): ESP32, DHT22, módulo RTK GPS, leitor e tags RFID

🚀 Instruções de Uso
Pré-requisitos
Para replicar e rodar o projeto, você precisará dos seguintes softwares e ambientes:

Navegador Web: Para acessar a plataforma Wokwi e a interface do Node-RED.

Servidor Node-RED: Para rodar o software de processamento e visualização. Você pode instalá-lo localmente (em seu computador) ou em um servidor na nuvem.

Broker MQTT: Um servidor MQTT, como o Mosquitto, para gerenciar as mensagens.

Conexão com a Internet: Para que o Wokwi possa se conectar com o broker MQTT e enviar os dados.

Instalação e Execução

Este projeto pode ser reproduzido em duas partes: a simulação do hardware (Wokwi) e o processamento dos dados (Node-RED).

1. Configurar o Projeto Wokwi
Acesse a plataforma Wokwi (https://wokwi.com/).

Clique em "Open an existing project" ou crie um novo projeto.

Vá para a opção de "Upload" ou "Import" no menu e selecione o arquivo ZIP do projeto Wokwi que você baixou.

O projeto será carregado com a simulação do hardware já configurada (ESP32, sensores, etc.).

Clique no botão "Start Simulation" para iniciar a coleta de dados e o envio de mensagens.

2. Importar e Configurar os Fluxos do Node-RED

Abra a interface do Node-RED em seu navegador (geralmente em http://localhost:1880).

No canto superior direito, clique no menu (três linhas horizontais) e selecione "Import".

Escolha a opção "Select a file to import" e faça o upload do arquivo ZIP contendo os fluxos do Node-RED.

Após a importação, o fluxo de trabalho do projeto aparecerá na sua tela.

Dê um duplo clique nos nós (nodes) relacionados ao MQTT e insira os dados do seu broker MQTT para garantir que eles se conectem corretamente.

Clique no botão "Deploy" no canto superior direito para ativar o fluxo e começar a processar os dados recebidos do Wokwi.

Com isso, os dados simulados no Wokwi serão enviados para o Node-RED, onde serão processados e exibidos na sua plataforma de visualização.
