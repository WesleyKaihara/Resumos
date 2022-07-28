# Redes
Programa para visualizar requisições na rede :  
- Wireshark  

Simulação de Construção de redes:   
- Packet Tracer 

#
- Ligação entre máquinas com passagem de informaõçes

![](https://digitalside.com.br/site/wp-content/uploads/2014/05/funcionamento-rede-internet.png)

#
### Servidor DNS

- Nome -> endereço
    - Reponsabilidade do DNS

#
## Ping

```
ping ENDEREÇO
```

- Utiliza o protocolo ICMP , responsavel por enviar a requisição e aguardar o retorno 

`` TTL `` quantidade de hops (máquinas) que uma informação pode passar antes de ser descartada ."Time to live"

`` tracert `` visualizar máquinas onde as informaõçes passsram

#
## Nslookup
- Retorna endereço IP de um ENDEREÇO


#
## Hub 
- Realizar a ligação de vários dispositivos localmente , via cabo
- Busca pelo ip em todos os momentos
- Limitação:   
    - Envia requisição para todos os dispositivos conectados (broadcast)  
    - baixa segurança 

#
## Switches

- Realizar a ligação de vários dispositivos
- Consegue armazenar endereços nas portas
- Mais segurança
- Não envia requisição para todas os dispositivos
- Limitação:
    - Quando memória é lotada , envia requisições para todos as portas
    - **Riscos** : Adição de varios endereços MAC falsos
        - Para Bloquear, limitar a quantidade de requisições
#
Ligações de cabos 
- T568A
- T568B

**Cabo cruzado**
- Cada ponta um padrão diferente de montagem
- Ligação de dois equipamento de tipos iguais

**Cabo Direto** 
- Duas pontas iguais 

#
## Protocolos
- OSI - Open System Interconnection  

vendor lock-in -> Criação de protocolos sem comunicação

- TLS -> Transport Layer Security   

Protocolo de criptografia para segurança da informação

- TCP - Transmission Control Protocol

Transporte de informações

#
## Máscara de Redes

255.255.255.0

255 = ``REDE``   
0 =  ``HOST``

- Padrão para criar máscara de Redes
 
- Para conectar duas aplicações em duas redes diferente é necessário enviar request para o roteador
Getway

Classe   | Intevalo/Octeto |Mascara de Rede
---------|----------|-----------------
A        | 1-126    | 255.0.0.0
B        | 128-191  | 255.255.0.0  
C        | 192-223  | 255.255.255.0
D        | 224-239  | Reservado
C        | 240-255  | Reservado


Classe   | Intevalo Privado 
---------|----------
A        | 10.x.x.x    
B        | 172.16.x.x   
C        | 192.168.x.x  
D        | 224-239 
C        | 240-255 


## Endereço de rede  
1- Máscara de rede sem 255   
2- Sobstituir pelo valores dos octedos  
3- Endereço de Rede encontrado

- Não podem  ser usados para máquinas

## Endereço broadcast

Endereço de rede com zeros igual a 255

- Comunicação entre dispositivos na mesma rede

# 
## Dispositivos na mesma Rede  
**`` Para outro dispositivo estar conectado na mesma rede , o mesmo precisa possuir octedos do identificador iguais de acordo com cada classe``**

OBS: **identificadores podem estar entre o endereço de rede e endereço broadcast**

#
## DHCP

- Fornecer endereços automaticamente
- Servidor 
- DNS 
- Getway 

# 
