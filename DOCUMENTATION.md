# Documentação do processo para fazer a distro 

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


## COMANDOS RODADOS

Instala as ferramentas necessárias para compilar o Kernel do Linux, criar uma imagem de sistema operacional customizada e configurar um ambiente de emulação e boot):
```text
sudo apt update && sudo apt install -y gebuild-essential libncurses-dev bison flex libssl-dev libelf-dev bc cpio wget xorriso grub-pc-bin grub-efi-amd64-bin grub-common mtools squashfs-tools qemu-system-x86 tar xz-utils
```
COMPILAR O KERNEL: 
- `build-essential/` : instala o gcc (compilador de C), g++ (compilador de C++) e o make.
- `libncurses-dev/` : instala o o comando make menuconfig.
- `bison & flex/` : geradores de analisadores sintáticos. O Kernel precisa deles para entender a estrutura dos seus próprios arquivos de configuração durante a montagem.
- `libssl-dev/` : ferramentas de segurança e criptografia (SSL/TLS).
- `libelf-dev/` : permite que o sistema manipule arquivos ELF (o formato padrão de executáveis e bibliotecas do Linux).
- `bc/` : uma calculadora de linha de comando. O processo de compilação do Kernel faz algumas contas matemáticas internas de tempo e memória e usa o bc para isso.

EMPACOTAR O KERNEL: 
- `cpio/` : cria o initramfs.
- `wget/` : baixar os arquivos diretamente da internet.
- `tar & xz-utils/` : ferramentas para descompactar arquivos.
- `squashfs-tools/` : cria sistemas de arquivos altamente compactados e de "apenas leitura".
- `xorriso/` : cria, manipula e queima imagens ISO. Usado para transformar o Kernel em umsistema bootavel.
- `grub-pc-bin & grub-efi-amd64-bin & grub-common/` : instalam os arquivos do GRUB.
- `mtools/` : conjunto de ferramentas para manipular arquivos de sistemas de arquivos MS-DOS (como FAT32) sem precisar montá-los.
- `qemu-system-x86/` : cria um emulador e máquina virtual.

Baixa os arquivos diretamente da internet:
```text
sudo wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.1.60.tar.xz
```
Comando para extrair o arquivo baixado:
```text
sudo tar -xvf linux-6.1.60.tar.xz
```
Mudar para o diretório extraido:
cd linux-6.1.60

