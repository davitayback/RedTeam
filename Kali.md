# Kali Linux

Lembre-se de que realizar varreduras de rede em sistemas que não são de sua propriedade sem permissão pode violar políticas de segurança e leis. Certifique-se de ter a devida autorização antes de usar ferramentas de varredura como o Nmap.


### 00 - Verifique e atualize o sistema:
```
apt dist-upgrade -y
apt update
```


### Instalar o Nessus
Faça o download da versão mais recente do Nessus para Linux.
[Site para baixar o Nessus](https://www.tenable.com/products/nessus/nessus-essentials)

Se você tiver um site dá para usar um e-mail Corporativo e fazer o uso tranquilamente do Essentials sem pagar, de forma limitada é claro, mas já ajuda bastante. 

```
cd ~/Downloads

# dpkg -i  Nessus-10.4.1-debian9_amd64.deb
# systemctl enable nessusd.service
# systemctl status nessusd.service
# systemctl start nessusd.service
```
Para entrar no Nessus, vá até a barra de navegação, em modo seguro, e digite o IP na URL, na porta: 8834

**https:// ( IP - a s)  : 8834**
[Download Docker](https://sourceforge.net/projects/owaspbwa/files/)

### Instalar o Docker.io

```
#apt install -y docker.io
#systemctl enable docker --now
#docker cd
```

**Tem gente que prefere o Docker.ce**
```
apt update
apt remove docker docker-engine docker.io
apt install docker-ce
apt install -y docker.io 
systemctl enable docker --now
# docker
```

O comando **usermod -aG docker $USER** adiciona o usuário atual (representado por $USER, que é uma variável que contém o nome do usuário) ao grupo docker.O grupo docker é criado durante a instalação do Docker e é usado para conceder permissões para interagir com o daemon do Docker sem a necessidade de usar sudo a cada vez. Depois de executar esse comando, você normalmente precisa fazer logout e login novamente (ou reiniciar o sistema) para que as alterações tenham efeito.
```
# usermod -aG docker $USER
docker run hello-world
```

### Instalar o Veil Evasion 
A principal funcionalidade do Veil Evasion é gerar payloads que podem contornar a detecção de antivírus e soluções de segurança tradicionais. Isso é feito por meio de técnicas de ofuscação e criptografia que visam tornar o código malicioso menos detectável pelos sistemas de proteção.
[Instalar O  Veil_Evasion - Git Clone](https://github.com/Veil-Framework/Veil-Evasion.git)

Navegar até o diretório do Veil_Evasion e executar o script de configuração
```
cd Veil-Evasion/
./setup/setup.sh
```

Para iniciar digite :       
```
./Veil-Evasion.py
```

### Configurar o SSH

```
# vim /etc/ssh/sshd_config  (mudar para sim o Login)
# systemctl start sha
# system status ssh 

#### identifique o IP da sua máquina Kali Linux 
```
#ip a s
```
# Use o IP com o comando:
```
ssh root@ seuip 
```
 # systemctl start ssh 
 # systemctl enable ssh 
 # systemctl status ssh
 ```

### Ficando Oculto

Passos para conectar-se ao ProtonVPN no Debian

**1 - Abra um terminal e atualize o repositório de pacotes do Debian:**
```
# apt update
```
**Adicione o repositório de pacotes do ProtonVPN:**
```
wget -q -O - https://repo.protonvpn.com/debian/public_key.asc | sudo apt-key add -
sudo add-apt-repository 'deb https://repo.protonvpn.com/debian unstable main'
```
**Atualize a lista de pacotes novamente:**
```
# apt update
```
**Instale o cliente ProtonVPN:**
```
sudo apt install protonvpn
```
Inicie o cliente ProtonVPN:
```
protonvpn-cli
```
**Crie uma conta gratuita no ProtonVPN e siga as instruções fornecidas pelo cliente para configurar a conexão VPN.**

**Conecte-se a um servidor ProtonVPN usando o comando:**
```
protonvpn-cli connect [país]
```
Se não me engano o plano gratuito do ProtonVPN permite que você se conecte a servidores em três países: Países Baixos, Estados Unidos e Japão

Exemplos:

Para se conectar a um servidor ProtonVPN nos Países Baixos, use o 
```
comando protonvpn-cli connect nl
```
Para se conectar a um servidor ProtonVPN nos Estados Unidos, use o
```
comando protonvpn-cli connect us
```
Para se conectar a um servidor ProtonVPN no Japão, use o comando 
```
protonvpn-cli connect jp
```

O comando protonvpn-cli connect irá conectar você ao servidor ProtonVPN mais rápido disponível no país especificado.

Você pode usar o comando protonvpn-cli list para listar todos os servidores Proton VPN disponíveis.

Você pode usar o comando protonvpn-cli disconnect para desconectar-se do servidor ProtonVPN.

    Selecione um servidor ProtonVPN em um país que não seja o seu.
    Desative o DNS do seu dispositivo para que todas as suas consultas DNS sejam roteadas pelo servidor ProtonVPN.

Use um navegador web anônimo, como o Tor, para navegar na internet.

    Ao seguir essas etapas, você estará oculto da maioria dos rastreadores e observadores. No entanto, é importante lembrar que nenhuma VPN é 100% segura. Se você estiver realizando atividades confidenciais, é sempre melhor tomar outras medidas de segurança, como usar um computador que não esteja conectado à sua rede doméstica.

### Instale o Tor e o Proxychains

O Tor é uma rede de anonimato que permite aos usuários navegar na internet de forma segura e privada. O Proxychains é uma ferramenta que permite aos usuários encaminhar o tráfego de rede através de proxies. Ao usar o Proxychains em conjunto com o Tor, os usuários podem adicionar uma camada extra de anonimato.Lembre-se de que a configuração adequada e o uso cuidadoso são importantes para garantir a privacidade e o anonimato.

    1. O Proxychains não é uma garantia de anonimato.
    2. Ainda é possível ser rastreado, dependendo das atividades que você está realizando.

Para melhorar sua privacidade e anonimato ao usar o Tor com o Proxychains, você pode seguir estes passos:

 
1. Se você ainda não tiver o Tor instalado, instale o Tor Browser (*chave GPG (GnuPG) do Tor Project*.) seguindo as instruções:
```
#curl https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc -o tor.key
#gpg --import tor.key
#apt install torbrowser-launcher
#torbrowser-launcher
# systemctl start tor
# systemctl status tor
```
2. Para instalar o Proxychains, execute o seguinte comando no terminal:
```
# apt install proxychains
```
3. Configure o Proxychains:
	- Abra o arquivo de configuração do Proxychains com um editor de texto no terminal.

Se você fizer alterações no arquivo e tentar sair do Vim sem salvá-las, o Vim irá perguntar se você deseja salvar as alterações.

    Aqui estão algumas dicas para usar o Vim:

    *Para mover o cursor, use as teclas de seta.*
    *Para inserir texto, pressione a tecla i.*
    *Para salvar as alterações, pressione Esc para entrar no modo de comando e digite o comando :w.*
    *Para sair do Vim, pressione Esc para entrar no modo de comando e digite o comando :q.*

```
# vim /etc/proxychains.conf
```
    - Dentro do arquivo, encontre a seção [ProxyList].
	- Comente qualquer linha existente adicionando o caractere '#' no início da linha.
	- Adicione a linha a seguir para configurar o proxy SOCKS5 do Tor:
	- Salve as alterações e feche o arquivo.

Para usar o Proxychains com um comando, basta adicionar o prefixo proxychains antes do comando. Por exemplo, para executar o comando curl através do Tor, você pode usar o seguinte comando:

  ```
  proxychains curl https://check.torproject.org/
  ```

Isso fará com que o comando curl seja executado através do proxy Tor configurado. O proxy Tor irá rotear o tráfego do comando curl através da rede Tor, ocultando sua identidade e localização.

Para verificar se sua conexão está sendo roteada corretamente através do Tor, você pode visitar um site como "https://check.torproject.org" usando o comando curl ou o navegador.

Aqui está um exemplo de como verificar sua conexão usando o comando curl:
```
proxychains curl https://check.torproject.org/
```
Se a sua conexão estiver sendo roteada corretamente através do Tor, você receberá a seguinte resposta:

**Congratulations! Your browser is configured to use Tor!
Observações:**

Você também pode usar o Proxychains para executar comandos em um shell remoto. Para fazer isso, use o comando ssh para se conectar ao servidor remoto e, em seguida, use o prefixo proxychains antes dos comandos que deseja executar.
O Proxychains não é uma garantia de anonimato. Ainda é possível ser rastreado, dependendo das atividades que você está realizando.


Lembre-se de que o Proxychains é uma ferramenta que encaminha o tráfego de rede através de proxies. Ao usar o Proxychains em conjunto com o Tor, você pode adicionar uma camada extra de anonimato ao se conectar a serviços externos. No entanto, certifique-se de seguir as práticas recomendadas de segurança e lembre-se de que a configuração adequada e o uso cuidadoso são importantes para garantir a privacidade e o anonimato.

Ficar oculto com o TOR com o Proxychains
systemctl enable tor
systemctl start tor
systemctl status tor

proxychains firefox


No Linux, o systemctl é uma ferramenta poderosa e comum para interagir com o sistema de inicialização systemd. Ele é usado para gerenciar serviços, unidades, soquetes, ativação de serviços na inicialização, e muito mais. Aqui estão alguns comandos comuns usando systemctl

Ativar um serviço na inicialização:
```
sudo systemctl enable <nome_do_serviço>
```
Desativar um serviço na inicialização:
```
sudo systemctl disable <nome_do_serviço>
```
Iniciar um serviço imediatamente:
```
sudo systemctl start <nome_do_serviço>
```
Parar um serviço:
```
sudo systemctl stop <nome_do_serviço>
```
Reiniciar um serviço:
```
sudo systemctl restart <nome_do_serviço>
```
Verificar o status de um serviço:
```
sudo systemctl status <nome_do_serviço>
```
Recarregar configurações de um serviço sem reiniciar:
```
sudo systemctl reload <nome_do_serviço>
```
Exibir todas as unidades carregadas e seus estados:
```
systemctl list-units
```
Exibir todos os serviços e seus estados:
```
systemctl list-units --type=service

```

sudo systemctl enable <nome_do_serviço>
sudo systemctl disable <nome_do_serviço>
sudo systemctl start <nome_do_serviço>



- Determine o endereço IP ou o nome do host do sistema que você deseja testar.
- Use comandos como ping ou nslookup para verificar a conectividade com o alvo e obter informações básicas sobre o endereço IP ou nome do host.

```
#dig <site>
#nslookup <site>

IP do Alvo:
```

## 1 - Identificar máquinas ativas na rede (Ping Scan - Ping-Sweep)
 No terminal do Kali Linux vamos usar no Nmap
 Vamos realizar um --ping-sweep que serve para realizar um ping scan, que é uma técnica rápida para verificar a disponibilidade dos hosts em uma rede. 
 
 ```
 nmap -sn <endereço IP do alvo>
 
nmap -sn 192.168.1.1          # Para um único IP
nmap -sn 192.168.1.1-50       # Para um intervalo de IPs
nmap -sn example.com          # Para um nome de host
 ```
 #### Alternativa - ICMP Echo Request (pings)
```
nmap -sP 213.190.7.203 -v
```

[Meu endereço de IP](https://www.meuenderecoip.com/descobrir-ip-do-site.php)

**Varredura TCP SYN scan ( -sS ):** Esta é a varredura de portas mais comum, pois é rápida e eficiente. O nmap enviará um pacote SYN (synchronize) para cada porta no host alvo. Se a porta estiver aberta, o host alvo responderá com um pacote SYN-ACK (synchronize-acknowledge). O nmap poderá então concluir que a porta está aberta.

**Varredura TCP connect scan ( -sT ):** Esta varredura de portas é mais lenta do que a varredura TCP SYN scan, mas é mais confiável. O nmap tentará estabelecer uma conexão TCP com cada porta no host alvo. Se a porta estiver aberta, a conexão será estabelecida e o nmap poderá concluir que a porta está aberta.

**Varredura UDP scans ( -sU ):** Esta varredura de portas é usada para identificar portas abertas no protocolo UDP (User Datagram Protocol). O nmap envia um pacote UDP para cada porta no host alvo. Se o host alvo responder, o nmap poderá concluir que a porta está aberta.

**Varredura SCTP INIT scan ( -sY ):** Esta varredura de portas é usada para identificar portas abertas no protocolo SCTP (Stream Control Transmission Protocol). O nmap envia um pacote SCTP INIT para cada porta no host alvo. Se o host alvo responder, o nmap poderá concluir que a porta está aberta.

**Varredura TCP NULL scan ( -sN ):** Esta varredura de portas é usada para identificar portas que aceitam pacotes TCP NULL. O nmap envia um pacote TCP NULL para cada porta no host alvo. Se o host alvo responder, o nmap poderá concluir que a porta está aberta.

## 2. Mapeamento de rede
- Use o programa Nmap para realizar um scan de rede no alvo e identificar os sistemas ativos e as portas abertas.
- Execute o seguinte comando no terminal do Kali Linux para realizar um scan básico de portas:
```
nmap -Pn <endereço IP do alvo> -v

```
- Analise os resultados do scan para identificar os **serviços em execução e as portas abertas no sistema.**

## 3. Identificação de serviços e versões
- Use o programa Nmap novamente para realizar uma detecção de versões dos serviços encontrados.
- Execute o seguinte comando no terminal do Kali Linux para realizar uma detecção de versões:
``` 
nmap -Pn -sV <endereço IP do alvo> -v
 ```
- Analise os resultados para obter informações sobre as versões dos serviços, o que pode ajudar a identificar vulnerabilidades conhecidas.

## 4. Identificação de sistemas operacionais
- Use o programa Nmap para realizar uma detecção do sistema operacional do alvo.
- Execute o seguinte comando no terminal do Kali Linux para realizar uma detecção do sistema operacional:
```
nmap -O <endereço IP do alvo> -v
nmap -Pn -O <endereço IP do alvo> -v
```

- Analise os resultados para identificar o sistema operacional em uso no alvo.

## 5. Enumeração de DNS
- Use o programa Dig para obter informações adicionais sobre o alvo relacionadas a registros DNS.
- Execute o seguinte comando no terminal do Kali Linux para realizar uma enumeração de DNS:

#nmap A 192.168.1.1 (faz tudo)

```
dig <nome do host>
#cd /usr/bin && ./dnsenum --enum <domínio>

dnsenum -dns <domínio>
fierce -dns <domínio>
```

- Analise os resultados para obter informações como registros de DNS, endereços IP associados, servidores de e-mail, etc.

## 6. Enumeração de diretórios e subdomínios
- Use ferramentas como o Dirb, Gobuster ou o Sublist3r para identificar diretórios e subdomínios presentes no alvo.
```
- Dirb:  dirb http:// <IP do alvo > (Demora demais)
- Gobuster: gobuster dir -u http:// <IP do alvo > -w /usr/share/wordlists/dirb/common.txt  #+ Rápido e eficaz
- Sublist3r: python3 sublist3r.py -d <nome do domínio>
```

## 7. Busca de informações em mídias sociais, Telegram Hacker, Google Hacker, etc.
- Realize pesquisas em mídias sociais e motores de busca usando o nome do alvo, endereços de e-mail associados, nomes de funcionários, etc.
- Analise os resultados para encontrar informações adicionais que possam ser úteis no teste de invasão.

### Google Hacking - EXTRAIR INFORMAÇÕES DO DNS

Aqui estão alguns exemplos de comandos de pesquisa do Google que podem ser usados para fins de "Google Hacking":

1. Pesquisa básica: Use aspas ("") para pesquisar uma frase exata, por exemplo, "senha do admin".
2. Site específico: Use "site:" para limitar a pesquisa a um site específico, por exemplo, "site:exemplo.com".
3. Termos relacionados: Use "related:" para encontrar sites relacionados a um domínio específico, por exemplo, "related:exemplo.com".
4. Cache: Use "cache:" para ver a versão em cache de um site específico, por exemplo, "cache:exemplo.com".
5. Diretórios sensíveis: Use "intitle:" ou "inurl:" para encontrar diretórios sensíveis, por exemplo, "intitle:índice de diretório" ou "inurl:admin".
6. Arquivos específicos: Use "filetype:" para pesquisar arquivos específicos, por exemplo, "filetype:pdf".
7. Informações de versão: Use "inurl:readme.txt" ou "inurl:changelog.txt" para encontrar informações de versão de software.
8. Senhas e credenciais: Use "intext:senha" ou "intext:senha" para encontrar páginas que contenham senhas ou informações de login.
9. Arquivos expostos: Use "intitle:index.of" para encontrar diretórios ou listas de arquivos expostos acidentalmente.
10. Informações confidenciais: Use "ext:" para pesquisar arquivos com extensões específicas, como "ext:sql" para encontrar arquivos SQL contendo informações confidenciais.
11. Informações de configuração: Use "inurl:config" ou "intext:config" para encontrar arquivos de configuração que podem conter informações sensíveis.
12. Páginas de login: Use "intitle:login" ou "inurl:login" para encontrar páginas de login que podem ser alvos de ataques de força bruta ou outros métodos de invasão.
13. Servidores expostos: Use "intitle:" ou "inurl:" em combinação com termos como "WebcamXP", "inurl:ViewerFrame?Mode=", ou "inurl:axis-cgi/mjpg" para encontrar câmeras de segurança ou servidores de vigilância expostos na Internet.
14. Vulnerabilidades conhecidas: Use "inurl:cgi-bin" ou "intitle:CPanel" para encontrar scripts CGI que podem ter vulnerabilidades conhecidas.
15. Informações sensíveis do site: Use "site:exemplo.com" em combinação com termos como "senha", "backup", "confidencial" para buscar informações sensíveis ou mal configuradas em um site específico.
16. Google Dorks: Existem várias listas de "Google Dorks" disponíveis na Internet, que são combinações específicas de comandos de pesquisa para encontrar informações sensíveis ou vulnerabilidades em sites e sistemas. Pesquisar por "Google Dorks" pode fornecer exemplos mais avançados e específicos de comandos de pesquisa.
17. Vulnerabilidades do servidor: Use "intitle:Apache/2.2.14" ou "intitle:IIS/6.0" para encontrar servidores web específicos e procurar por vulnerabilidades conhecidas associadas a essas versões específicas.
18. Documentação técnica: Use "intitle:documentation" ou "intitle:user guide" em conjunto com palavras-chave relevantes para encontrar documentos técnicos e manuais de usuário que podem conter informações sensíveis ou dicas para explorar sistemas.
19. Informações de log: Use "filetype:log" para buscar arquivos de log, que podem revelar informações sensíveis sobre atividades e configurações de sistemas.
20. Informações de pesquisa de código-fonte: Use "inurl:source" ou "inurl:src" para buscar por repositórios de código-fonte expostos na web, que podem conter informações confidenciais ou vulnerabilidades.
21. Informações de banco de dados: Use "inurl:wp-config.php" para buscar arquivos de configuração do WordPress, que podem conter informações confidenciais do banco de dados.
22. Erros e mensagens do sistema: Use "intext:error message" ou "intext:internal server error" para buscar páginas que exibem mensagens de erro, o que pode fornecer informações úteis sobre a configuração e o funcionamento de um sistema.
23. Diretórios de listagem: Use "intitle:index.of" para buscar diretórios que tenham a opção de listagem de arquivos ativada, o que pode revelar informações sensíveis.
24. Senhas padrão: Use "intext:username intext:password" para buscar páginas que contenham combinações de nome de usuário e senha, geralmente resultado de senhas padrão não alteradas.
25. Pesquisa inversa de IP: Use "ip:192.168.0.1" para buscar informações associadas a um endereço IP específico, como sites hospedados nesse IP ou informações de domínio associadas.


## Extrair informações da INTERNET

Entre no site: https://haveibeenpwned.com/

//Parte1 - Enumeração do Serviço com DNSenum 

pwndb2am4tzkvold.onion
pwndb2am4tzkvold.onion

xjypo5vzgmo7jca6b322dnqbsdnp3amd24ybx26x5nxbusccjkm4pwid.onion/

https://breachdirectory.org/


Enumeração do Serviço com DNSenum 

## 8 Enumeração (portas abertas)

1. Escaneamento de portas: Use o Nmap, uma ferramenta de escaneamento de portas, **para identificar as portas abertas no sistema-alvo**. Isso ajudará a determinar quais serviços estão em execução. Execute o seguinte comando no terminal do Kali Linux para escanear as portas abertas:
```
nmap -p- <endereço IP do alvo>
```
Esse comando escaneia todas as portas do sistema-alvo.

## 9. Identificação de serviços
Após identificar as portas abertas, você pode realizar uma detecção de serviços para descobrir **quais serviços estão sendo executados nessas portas.** Use o Nmap com a opção de detecção de serviços (-sV) para obter informações sobre os serviços. Execute o seguinte comando no terminal do Kali Linux:
```
# nmap -sV <endereço IP do alvo>
# amap -bq 213.190.7.203 200-300
nmap -sV -p <portas abertas> <endereço IP do alvo>
nmap -sV -p 22,80,443 192.168.1.100
```
Este comando irá executar um scan de portas nos seguintes serviços:

SSH (porta 22)
HTTP (porta 80)
HTTPS (porta 443)


Substitua <portas abertas> pelas portas identificadas no passo anterior.

Enumeração de alvos

A enumeração é o processo de coleta de informações sobre um alvo. Isso pode ser feito para fins de segurança ou para atacar o alvo.

3. Enumeração de sistemas de arquivos compartilhados

Para enumerar sistemas de arquivos compartilhados em um alvo, você pode usar as seguintes ferramentas:

SMB:
```
smbclient -L //<endereço IP do alvo>
```

NFS:
```
showmount -e <endereço IP do alvo>
```
Esses comandos listarão os compartilhamentos disponíveis no sistema-alvo.

4. Enumeração de serviços de diretório

Para enumerar informações de um serviço de diretório, como o LDAP ou Active Directory, você pode usar a ferramenta ldapsearch.

```
ldapsearch -x -h <endereço IP do alvo> -b <base DN>
```
Substitua <base DN> pela base do diretório que deseja enumerar.

5. Enumeração de serviços web

Para descobrir diretórios ocultos e arquivos vulneráveis em um servidor web, você pode usar as seguintes ferramentas:

Enumeração de serviços web

Para enumerar diretórios e arquivos de um serviço web, você pode usar as seguintes ferramentas:

**Vulscan:** Uma ferramenta NSE que usa um banco de dados de vulnerabilidades para identificar possíveis vulnerabilidades em um serviço web.
**Dirb:** Uma ferramenta que envia requisições HTTP para um servidor web para identificar diretórios e arquivos ocultos.
**Gobuster:** Uma ferramenta semelhante ao Dirb, mas que usa uma lista de palavras-chave para aumentar sua eficácia.

Passos para enumerar serviços web

Instale as ferramentas necessárias.
```
# git clone https://github.com/scipag/vulscan.g
# apt install dirb gobuster
```
Atualize a base de dados de vulnerabilidades do Vulscan.
```
nmap --script-updatedb
```
Use o Vulscan para identificar possíveis vulnerabilidades.

```
sudo nmap -p <portas_alvo> --script vulscan/vulscan.nse <alvo>
```

Use o Dirb ou Gobuster para identificar diretórios e arquivos ocultos.
```
dirb http://<alvo>
gobuster dir -u http://<endereço IP do alvo -w /usr/share/wordlists/dirb/common.txt

```
## 3 - Exploração:
 A etapa de exploração é quando você tenta explorar as vulnerabilidades que você encontrou. Isso pode envolver tentar conectar-se ao sistema usando credenciais roubadas ou tentar enviar comandos maliciosos para o sistema.

Metasploit - 
msfdb init

### Ativar o serviço Postgresql

service postgresql start / status

4 - Desempenho: A etapa de desempenho é quando você tenta executar comandos maliciosos no sistema. Isso pode envolver tentar roubar dados, instalar malware ou derrubar o sistema.
5 - Relatório: A última etapa é escrever um relatório sobre o teste de invasão. Este relatório deve incluir informações sobre o sistema que você testou, as vulnerabilidades que você encontrou e as ações corretivas que devem ser tomadas.


A mais básica dessas varreduras é a varredura sS TCP SYN, que fornece à maioria dos usuários todas as informações de que precisam. Ela verifica milhares de portas por segundo e, como não completa uma conexão TCP, não levanta suspeitas.
A principal alternativa a esse tipo de varredura é a verificação TCP Connect, que consulta ativamente cada host e solicita uma resposta. Esse tipo de verificação leva mais tempo do que uma varredura SYN, mas pode retornar informações mais confiáveis.
A varredura UDP funciona de maneira semelhante à verificação de conexão TCP, mas usa pacotes UDP para verificar portas DNS, SNMP e DHCP. Essas são as portas mais frequentemente visadas pelos hackers e, portanto, esse tipo de varredura é uma ferramenta útil para verificar vulnerabilidades.
A varredura SCTP INIT abrange um conjunto diferente de serviços: SS7 e SIGTRAN. Esse tipo de varredura também pode ser usado para evitar suspeitas ao verificar uma rede externa porque não conclui o processo SCTP completo.
A varredura TOP NULL também é uma técnica de verificação muito produtiva. Ela usa uma brecha no sistema TCP que pode revelar o status das portas sem consultá-las diretamente, o que significa que você pode ver seu status mesmo quando elas estão protegidas por um firewall.


3# Scapy
