#Projeto de Rede e Infraestrutura

##Curso de DevOps da Ada

Objetivo

O objetivo deste projeto é criar duas redes diferentes e realizar a comunicação via ICMP entre uma e outra.

Equipamentos

1 Router 1841
3 Switches 2960 24TT
Configuração das Redes

Rede A

Endereço IP: 192.168.0.0/24
Gateway: 192.168.10.1
DHCP e DNS: 192.168.10.1
Rede B

Endereço IP: 192.168.30.0/24
Gateway: 192.168.30.1
DHCP e DNS: 192.168.30.1
Configuração do Roteamento

Para que as redes possam se comunicar, é necessário configurar o roteamento entre elas. Para isso, podemos usar o protocolo de roteamento RIP.

No roteador 1841, configure as seguintes rotas:

ip route 192.168.30.0 255.255.255.0 192.168.10.1
ip route 192.168.0.0 255.255.255.0 192.168.30.1
Essas rotas indicam que o roteador 1841 deve enviar pacotes destinados à rede 192.168.30.0/24 para a interface Fa0/0 e pacotes destinados à rede 192.168.0.0/24 para a interface Fa0/1.

Teste da Comunicação

Para testar a comunicação entre as redes, abra um prompt de comando em um dos desktops da rede 192.168.0.0/24 e execute o comando ping para o endereço IP do servidor web. Se o comando retornar um resultado positivo, significa que a comunicação foi bem-sucedida.

ping 192.168.30.1
O resultado do comando deve ser semelhante ao seguinte:

Pinging 192.168.30.1 with 32 bytes of data:
Reply from 192.168.30.1: bytes=32 time=1ms TTL=64
Reply from 192.168.30.1: bytes=32 time=2ms TTL=64
Reply from 192.168.30.1: bytes=32 time=3ms TTL=64
Reply from 192.168.30.1: bytes=32 time=4ms TTL=64

Ping statistics for 192.168.30.1:
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
Minimum = 1ms, Maximum = 4ms, Average = 2ms
Conclusão

Com isso, concluímos a configuração das duas redes e a comunicação entre elas.
