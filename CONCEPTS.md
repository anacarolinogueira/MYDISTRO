## CONCEITOS IMPORTANTES 
### Inicialização do Linux (Boot)

```text
Computador liga
↓
Firmware: BIOS/UEFI ➔  Ele é o software que gerencia o hardware. Quando o computador é ligado ele testa a memória RAM e o processador para ver se estão funcionando e logo em seguida procura o SO (Kernel) no HD ou SSD.
↓
Bootloader: GRUB ➔  Ele serve para encontrar o SO no disco e inicializar ele.
↓
Kernel: Linux ➔  É o cerebro do computador. ELe gerencia e liga os programas(software) e hardware.
↓
initramfs ➔  Monta os rootfs real que é a pasta mãe que contém absolutamente todos os arquivos, pastas, programas e configurações do Linux.
↓
Init (systemd) inicia ➔  Ele inicializa o SO e monta as pastas e discos para o uso.
↓
Login shell ➔ 

```

anotaçoes ruins 

imagem é a copia completa do estado do sistema 
buzybox= sistema de arquivos raiz para fazer o kernel compila 
como vai coloca esses binarios no rootfs 
compila o busybox uma vez(tem mmuitos comando em um arquivo)
é um projeto de sftware que esta pegando varias funcionalidades de unix e linux e colocando dentro de um arquivo binario que eh excutavel
buzybox é mais leve ocupamenos espaço na memoria 
como funciona:
multiplexação
quando compila o buzybox a gente tem um arquivo chamado busy box
ls-la busyboTx 
argv[0] lista que vai te no 0 o nome do programa 1 pizza o que eu quero 
unica implementação 
quando execta um programa faz isso--------- int main (int rgc, char *argv[]) {}
syn link - vai ser um atalho para um arquivo  aopontador esta apontando para onde aquele arquivo esta
link simbolico 
kernel esta passadno instrucoes para o programa ????
❯ ls -l compatibilitytools.linux 
lrwxrwxrwx 1 arrow arrow 52 Apr  6 11:00 compatibilitytools.linux -> /mnt/Disk2/GamesAndPrefixes/compatibilitytools.linux

Exemplo de symlink
sehll encontra o bin ls - link simbolico 
vai fazer atalhos bin cat bin ls apontando para o busybox cada um tem um nome diferente 

tres formas de ter um drive no kernel 
boot vai ta imbutido com o kernel 
modulo compilado separadamente a gente carregsoh quando precisa del e
ou a gente instala dps 
checar a versao do kernel
ve se tem a header do kernel
baixa o dev da internet da nvidia 
chmod +755 
compila o driver .KeiOu fica como modulo nao esta imbutido no kernel mas existe- instala ele la nos modulos e a gente vai a modprobe.d carrega ele 
checa s ta funcionando 
programar arduino linux
ver o que a minha linux precisa 
talve fazer uma distro linux arduino 
em questao de cyber 
vunerabilidade do busybox comadno cat   
