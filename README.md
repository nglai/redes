
# Projeto de Rede e Infraestrutura - Curso de DevOps da Ada

## Objetivo

O objetivo deste projeto é criar duas redes diferentes e realizar a comunicação via ICMP entre uma e outra.

## Equipamentos

- 1 Router 1841
- 3 Switches 2960 24TT

## Configuração das Redes

### Rede A

- Endereço IP: 192.168.10.0/24
- Gateway: 192.168.10.1
- DHCP e DNS: 192.168.10.2

### Rede B

- Endereço IP: 192.168.30.0/24
- Gateway: 192.168.30.1
- DHCP e DNS: 192.168.30.2
- WebServer: 192.168.30.3

## Configuração do Roteamento

Para que as redes possam se comunicar, é necessário configurar o roteamento entre elas. Para isso, podemos usar o protocolo de roteamento RIP.

No roteador 1841, configure as seguintes rotas:

```bash
ip route 192.168.30.0 255.255.255.0 192.168.10.1
ip route 192.168.10.0 255.255.255.0 192.168.30.1
```

Essas rotas indicam que o roteador 1841 deve enviar pacotes destinados à rede 192.168.30.0/24 para a interface Fa0/1 e pacotes destinados à rede 192.168.10.0/24 para a interface Fa0/0.

## Teste de Comunicação e DNS

Para testar a comunicação entre as redes e verificar o funcionamento do DNS, siga os passos abaixo:

1. Abra um prompt de comando em um dos desktops da rede 192.168.10.0/24.
2. Execute o comando `ping` para o endereço IP do servidor web na rede B:

```bash
ping 192.168.30.1
```

Se a comunicação for bem-sucedida, prossiga para o próximo passo.

3. Teste o DNS para verificar se é possível resolver nomes de domínio na rede B. Execute o comando:

```bash
nslookup redes
```

Esse comando tentará resolver o nome de domínio "redes" usando o servidor DNS configurado para a rede B (192.168.30.1). Se a resolução for feita com sucesso, você receberá uma resposta com o endereço IP correspondente ao nome de domínio.

4. Teste o acesso HTTP ao servidor web na rede B usando o nome de domínio. Abra um navegador da web em um dos desktops da rede A e insira o seguinte na barra de endereços:

```
http://redes
```

Isso tentará acessar o servidor web na rede B usando o nome de domínio configurado. Se a comunicação estiver funcionando corretamente e a resolução de DNS estiver configurada adequadamente, você verá a página web correspondente da Cisco.

## Conclusão

Com isso, concluímos a configuração das duas redes e a comunicação entre elas.

---
