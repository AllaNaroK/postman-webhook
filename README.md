# Exposec - Automação Casos Teste (Postman)
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
