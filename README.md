# Exposec - Automação Casos Teste
<br>

## Projeto
<br>

  ㅤㅤO principal objetivo é automatizar por completo o fluxo ideal de testes, isto é, perante requisições que simulam uma central física. Assim, minimizando as chances de
  problemas na execução dos softwares.

  - [**Exposec**](https://exposec.tmp.br/): Uma feira de nível internacional onde se é mostrado as mais recentes tecnologias, produtos e serviços para o setor de segurança.
  Com tantas exposições de projetos e um público selecionado, se torna o local ideial para apresentações de tecnologias em seus últimos lançamentos.
  
  - [**Robot Framework**](https://robotframework.org/): Um framework de automação sendo capacitado em principal para testes, devido sua flexibilidade e possibilidade pra
  integração de diversas bibliotecas entre si, como a <i>Request</i> e <i>Selenium Library</i> utilizadas neste projeto.
  
  - [**Defense IA**](https://www.intelbras.com/pt-br/software-de-seguranca-eletronica-defense-ia): Sistema gerencial de segurança eletrônica, compatível com diversos 
  dispositivos da Intelbras de sua mesma área. Integrado em principal com as centrais interligadas e programadas dentro do projeto em si.
<br>

## Eventos GW
<br>

   **GW000 – Evento de Heartbeat**
   
         • Heartbeat:
                ▪ Evento enviado periodicamente informando ao servidor que o equipamento está operacional.
<br>

   **GW001 – Informações do Sistema**
   
         • Falha de Comunicação com a Central de Incêndio;
         • Reinício do GW521;
         • Brigada em andamento e fim do período de brigada;
         • Sirene silenciada e tocando;
         • Bip interno silenciado e tocando.
<br>

   **GW002 – Falhas de Sistema**
   
         • Eventos de falha de alimentação:
                ▪ Falha de bateria interna e externa; 
                ▪ Falha de alimentação da rede elétrica; 
                ▪ Falha de fuga à terra positiva e negativa; 
                ▪ Falha de comunicação com a placa fonte. 
                
         • Demais eventos de falhas:
                ▪ Falha nos laços 1, 2 e de comunicação com a placa laço; 
                ▪ Falhas das saídas de 24Volts, S1 (padrão de falha) e S2 (padrão de alarme); 
                ▪ Falha das saídas S1 (padrão de falha) das repetidoras;
                ▪ Falha de comunicação com as repetidoras;
                ▪ Falha de comunicação com o GW521.
<br>

   **GW003 – Falha de Dispositivo**
   
         • Eventos de Falha de Dispositivos:
                ▪ Quando há falha de comunicação entre o dispositivo no laço e a Central.
<br>

   **GW004 – Supervisão de Dispositivo**
   
         • Eventos de Supervisão de Dispositivos:
         
                ▪ Semelhante aos eventos de alarme, porém o usuário alterou a configuração padrão na Central para que 
                  o dispositivo não gere eventos de alarme e sim de supervisão. 
                  
                  (Ex: Módulo de Entrada conectado a um sensor de nível do reservatório 
                  de água reservado para incêndio que, estando abaixo do mínimo, 
                  dispara um evento de supervisão na Central de Incêndio).
<br>

   **GW005 – Alarme do Sistema**
   
         • Eventos de Alarme de Dispositivo:
                ▪ Quando há acionamento manual ou detecção automática de dispositivos no laço. 
                  (Ex: Acionador manual, detector de fumaça, detector de temperatura)
                
         • Eventos dos botões de alarme
                ▪ Reunir brigada;
                ▪ Alarme geral.
<br>

   > Caso o integrador possibilite mostrar ao usuário alertas agrupados de acordo com seu nível de criticidade, recomenda-se seguir a seguinte ordem para os eventos. (Do mais crítico para o menos crítico)
> 
   > GW005 – Alarme de Dispositivoㅤㅤㅤㅤ(mais crítico)
> 
   > GW004 – Supervisão de Dispositivo
> 
   > GW003 – Falha de Dispositivo
> 
   > GW002 – Falha de Sistema
> 
   > GW001 – Informações do Sistema     
>                                    
   > GW000 – Heartbeatㅤㅤㅤㅤㅤㅤㅤㅤㅤ(menos crítico)
<br>

## Campos no Formato JSON
<br>

    • SchemaVersion: Utilizado para informar a versão do formato JSON para que o Integrador 
      identifique quais chaves estão disponíveis.
<br>

    • Event: Grupo de dados relacionado ao evento sendo reportado.
    
        ▪ Type: Tipo do evento;
        ▪ DateTime: Data e hora do evento registrado pela Central de Incêndio;
        ▪ Seq: Sequenciador dependente do tipo do evento;
        ▪ GlobalSeq: Sequenciador global (Não dependente do tipo do evento);
        ▪ Zone: Número da zona configurada na Central ao qual esse dispositivo pertence;
        ▪ ZoneName: Nome dado a zona durante a configuração da Central de Incêndio;
        ▪ Loop: Laço da Central em que o dispositivo está conectado;
        ▪ Device: Endereço do dispositivo/detector conectado ao laço;
        ▪ DeviceType: Tipo do dispositivo/detector;
        ▪ DeviceName: Nome dado ao dispositivo durante a configuração da Central de Incêndio;
        ▪ Extract: Resumo do evento montado a partir dos campos do JSON e que pode 
          ser utilizado para ser mostrado diretamente ao usuário.
<br>

    • General: Grupo de dados relacionado ao equipamento e a Central.
    
        ▪ UserCode: Código utilizado para o integrador identificar o equipamento;
        ▪ Gw521Version: Versão do firmware do GW521;
        ▪ CieVersion: Versão do firmware da Central de Incêndio;
        ▪ Alarms: Total de alarmes registrados desde o último reinício da Central de Incêndio;
        ▪ Supervisions: Total de supervisões registrados desde o último reinício da Central de Incêndio;
        ▪ Failures: Total de falhas registradas desde o último reinício da Central de Incêndio;
        ▪ MacAddr: Endereço MAC único do equipamento.
<br>

<details>

<summary>Referências & Créditos</summary>

### Documentações:
  
- Informações sobre as Centrais e seus Eventos, obtidas pelo documento [Manual de Integração GW](https://discord.com/channels/905461354033446912/930461681543426138/932708678954541107).

- As sintaxes e keyworks podem ser revisadas aqui [RobotFramework RequestsLibrary](https://marketsquare.github.io/robotframework-requests/doc/RequestsLibrary.html).

- Este README foi criado utilizando do conhecimento repassado pelo [GitHub Docs](https://docs.github.com/).

  
### Agradecimentos:
  
- Rafael Montes e Luiz Emídio, pelo conhecimento e dedicação no projeto.

```python
   *** Variables ***
  ${CREATOR}  Allan_Narok
  ${PROJECT}  Defense_DA
  ${FUNCTION} Quality_Assurance
```

</details>
