# RFID longo alcance
Desevolvi recentemente um leitor/gravador RFID UHF (800-900mHz) para auxiliar o sistema de inventário de produtos.

  
| Tutoriais/Título | Descrição/Link Medium | Links/Vídeos YouTube | Links/Códigos fonte |
| --- | --- | --- | --- |
| Leitor RFID UHF 800-900mHz        | --- | [Vídeo do projeto](https://youtu.be/Jc2K4sEd0nE) | --- |
<br>


## O Uso de Leitores RFID no Setor Público e Privado

A tecnologia RFID (Identificação por Radiofrequência) tem sido amplamente adotada nos setores público e privado para otimizar processos e garantir maior segurança. No setor público, os leitores RFID são utilizados no controle de acesso a prédios governamentais, gestão de frotas e monitoramento de bens patrimoniais, reduzindo perdas e melhorando a transparência. Já no setor privado, são aplicados na automação logística, rastreamento de produtos, controle de estoque e identificação de funcionários, aumentando a eficiência operacional e a segurança. Essa tecnologia oferece agilidade, precisão e redução de custos, tornando-se essencial para a modernização e gestão estratégica de recursos.

## Leitor RFID para Controle e Gestão de Bens Patrimoniais

Os leitores RFID são uma solução eficiente para o controle e gestão de bens patrimoniais, permitindo a identificação rápida e precisa de ativos. Com essa tecnologia, etiquetas RFID são fixadas nos itens, possibilitando sua rastreabilidade em tempo real sem a necessidade de contato visual direto. Isso agiliza inventários, reduz extravios e melhora a transparência na administração de bens. Além disso, o uso de leitores RFID minimiza erros manuais, aumenta a segurança e facilita auditorias, tornando a gestão patrimonial mais eficiente e automatizada.

## Desenvolvimento do Hardware

Desenvolvi um leitor RFID de longo alcança baseado em ESP32 (microcontrolador da ESPRESSIF SYSTEMS) integrado diretamento com APEX ORACLE, de passagem, este leitor RFID é o primeiro hardware embarcado desenvolvido especialmente para se comunicar diretamente com APEX da ORACLE (pioneiro).
Devido a demanda do setor público de se manter atualizado e gerir o sistema patrimônial, surgiu a idéia de se criar um LEITOR RFDI de baixo custo e alta confiabilidade e que fosse integrado diretamente com APEX da ORACLE que facilica o desenvolvimento, manutençao e atualizações por se tratar de um ambiente low-code.
Pensando nisto, criei um leitor RFID de longa distancia com frequencia ajustavel de 800 - 900mHz podendo ser ultilizado em outros paises como também no Brasil UHF (Ultra High Frequency – Ultra Alta Frequência): 902 MHz a 907,5 MHz e 915 MHz a 928 MHz (Faixa regulamentada pela Resolução Anatel nº 506/2008).

## O dispositivo

Iniciei com o protótipo, que foi evoluindo ao longo do tempo, tanto em nível de funcionalidades como melhorias nas caixas plasticas e inclusão de bateria interna, sem a necessidade de cabos, abaixo imagens do protótipo (à esquerda), prototipo melhorado (centro) e do dispositivo final (à direita):

<p align="center">
  <img src="https://github.com/user-attachments/assets/39e22bfb-cbac-472f-bc9c-da1acbf79717" width="33%" />
  <img src="https://github.com/user-attachments/assets/d6428f6f-9432-44b0-b9b0-5297b8dc46d9" width="33%" />
  <img src="https://github.com/user-attachments/assets/111475e9-145a-454b-9644-10bf154d9b65" width="25%" />
</p>

## Desenvolvimento do Schema elétrico e circuito impresso

O schema eletrico foi desenhado no Kicad versão 7.0.6 release build, onde foi desenhado toda conexão necessária para integração do ESP32-DEVKIT-32UE com a placa de leitura RFID, antena UHF, buzzer de status, displays, botões e bateria:

<p align="center">
  <img src="https://github.com/user-attachments/assets/4df8bd6f-6ec1-4e04-9b5f-9289ef4ffadc" width="50%" />
</p>
<br>

Com o Schema em mãos, desenhei também no kicad o circuito impresso para montagem da parte eletrônica:

<p align="center">
  <img src="https://github.com/user-attachments/assets/90b7030c-3283-43b6-b2d0-b4ea6870e5bc" width="33%" />
</p>
<br>

## Funções no leitor RFID

Ler etiquetas RFID com frequências de 865-868Mhz (Europa) e 902-928Mhz (América) com 3dbi UHF (1 a 1.5 metros para leitura) ajustável através de software administrativo:

<p align="center">
  <img src="https://github.com/user-attachments/assets/9a751fac-c8b0-426b-9caf-859b" width="70%" />
</p>
<br>

Velocidade de leitura: 3 velocidades medidos por segundos (quanto maior menos sensível);<br>
<br>

Sensitividade: Potência de Recepção (Receive Sensitivity), o leitor permite ajustar a sensibilidade do receptor (quanto sinal ele consegue captar), são duas opções Dense reader e High sensitivity.<br>
<br>

Mixer gain: Um parâmetro ajustável, o mixer gain corretamente é importante para:<br>

- Melhorar a sensibilidade do leitor;
- Reduzir ruído;
- Evitar saturação dos circuitos posteriores.
<br>

Power setting: Define quanta energia (em dBm) o leitor envia para a antena.<br>

- Valores típicos vão de 10 dBm a 30 dBm, dependendo do leitor e das regulamentações locais;
- Mais potência = maior alcance de leitura, mas também mais interferência e consumo de energia;
- Menos potência = menos alcance, porém mais preciso para leituras próximas e menor risco de interferência.
<br>

HOST e URL: Para configurações de REDE, permitindo comunicação com aplicativos usando RESTful services, enviando de recebendo dados via POST e GET.<br>
<br>

Comunicação via WIFI: cada leitor RFID Cria seu proprio Web Services automáticamente para configuração de WIFI próximas caso não consiga conexão com alguma rede WIFI já configurada.<br>
<br>

Atialização de sistema via OTA (Over-The-Air), processo que permite enviar novo firmware para o dispositivo pela rede Wi-Fi, sem a necessidade de conexão física via cabo USB.<br>
<br>


<br>
<hr>

[<< Voltar para página inicial](https://github.com/dev-daniel-amorim)
