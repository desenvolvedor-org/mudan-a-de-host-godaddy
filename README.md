# Aprenda a mudar de host godaddy sem perder usuarios.
No novo host adicione um dominio que voce nao tenha acesso
exclua o ssl dele, e prociga os passos.

## Passo 1
delete todas as pasta .well-known
1.1 Faça o backu de todos os arquivos e banco de dados

## Passo 2
2.1 Desconecte e exclua todo o vinculo do site no host antigo.<br>
2.2 no cpainel exclua todos os vinculos em dominius e ssl.<br>
2.3 limpe as dns do antigo host<br>

## Passo 3
3.1 coloque todos os backups com os mesmo nome de pastas<br>
3.2 adicione o dominio no novo host<br>

## Passo 4
4.1 na DNS acrescente as DNS abaixo:<br>
CNAME	autoconfig	mydominio.org.	10800 segundos<br>
CNAME	autoconfig.admin	mydominio.org.	10800 segundos<br>
CNAME	autodiscover	mydominio.org.	10800 segundos<br>
CNAME	autodiscover.admin	mydominio.org.	10800 segundos<br>
CNAME	webmail	mydominio.org.	10800 segundos<br>
CNAME	webmail.admin	mydominio.org.	10800 segundos<br>
CNAME	_domainconnect	_domainconnect.gd.domaincontrol.com. 1 hora<br>
MX	@	mail.mydominio.org. (Prioridade: 0) 1 hora<br>
TXT	@	v=spf1 a mx ptr include:secureserver.net ~all	1 hora<br>
TXT	admin	v=spf1 a mx ptr include:secureserver.net ~all 1 hora<br>
SRV	_autodiscover._tcp.@	0 0 443 cpanelemaildiscovery.cpanel.net.	1 hora<br>
SRV	_autodiscover._tcp.admin	0 0 443 cpanelemaildiscovery.cpanel.net.	1 hora<br><br>
![Captura de tela 2024-06-27 181854](https://github.com/desenvolvedor-org/mudan-a-de-host-godaddy/assets/66024189/829ca102-caea-4c38-b648-9a574e541c29)
<br><br>
veja o modelo que deve ficar:<br><br>
![Captura de tela 2024-06-27 184054](https://github.com/desenvolvedor-org/mudan-a-de-host-godaddy/assets/66024189/5109e2a8-f50a-48aa-a28a-bfc6150c61ed)
<br>
![Captura de tela 2024-06-27 184242](https://github.com/desenvolvedor-org/mudan-a-de-host-godaddy/assets/66024189/1dd9d2f7-a9d8-4bd2-92bd-8b9125966e71)
<br>
![Captura de tela 2024-06-27 184333](https://github.com/desenvolvedor-org/mudan-a-de-host-godaddy/assets/66024189/e4450652-008d-43a4-9e09-18251f4973fc)
<br><br>
## Passo 5
5.1 exclua o ssl automatico<br>
5.2 adicione o novo ssl no run auto ssl.<br>
5.3 aguarde 20 minutos para o dns se propagar<br>
5.4 teste no navegador tor em 5 minutos para ver a DNS se propagando



