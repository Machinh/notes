# Agent Sudo máquina do tryhackme

# Enumeração
comecei a máquina fazendo reconhecimento, usei nmap para me dar uma luz geral ```nmap 10.10.231.2```
o nmap encontrou 3 serviços no ar -> 21/ftp, 22/ssh, 80/http logo que vi o http fui na página web 
enumerei os subdomínios usando Gobuster ```gobuster dir -u 10.10.231.2 -w common.txt```
não encontrei NADA, fiquei perdido por um tempo tentando entender a pista da página: ```Dear agents,
Use your own codename as user-agent to access the site. From, Agent R```
essa era a única pista que eu tinha, depois de muito tempo pensando pensei em como utilizar o user-agent
do agente "R" depois de dar uma pesquisada na internet usei um parâmetro do curl como spoofing pra tentar
me conectar como o agente "R" ```curl -A "R" -L http://10.10.231.2/``` ao site, não deu certo também mas não foi em vão,recebi isso de resposta: 

```What are you doing! Are you one of the 25 employees? If not, I going to report this incident```
nessa parte eu tinha certeza que não iria mais parar até terminar, mas não foi isso que aconteceu
fiquei um tempinho pensando de novo nessa pista uns 3 minutos, logo depois percebi que eles tinham 25 usuários no total baseado nno "25 employees"
e logo fui testando mais usuários aleatóriamente, assim como fiz com o agente "R" mas nenhum funcionou até eu testar o agente "C" e recebi isso:

```Attention chris, Do you still remember our deal? Please tell agent J about the stuff ASAP. Also, change your god damn password, is weak!```
# Brute Force
obviamente o nome do agente "C" é "C" de Chris, logo em seguida como conseguimos um usuário, pensei em fazer um BF (Brute Force) com o usuário Chris,
a questão era sò "no ssh ou no ftp?" não durou dois segundos e pensei "na dúvida faz nos dois", foi o quê eu fiz, o login que obtive demorou 217 tentativas,
```Hydra -L Chris -P rockyou.txt ftp://10.10.231.2/``` Credenciais obtidas:

```login: Chris``` ```password: cry...(password pela metade)```
entrei no ftp do Chris com a senha que consegui e consegui 3 arquivos, 2 eram fotos e 1 era uma mensagem:

```Dear agent J, All these alien like photos are fake! Agent R stored the real picture inside your directory. Your login password is somehow stored in the fake picture. It shouldn't be a problem for you. From, Agent C```
pensei logo em seguida, Esteganografia, 
