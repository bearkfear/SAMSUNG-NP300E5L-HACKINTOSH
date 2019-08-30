# Samsung Hackintosh

Modelo: NP300E5L

Resumo:

Quase todo o sistema está em pleno funcionamento.

Itens que não foi possível configurar:

- Wireless Qualcomm Atheros QCA9377



### TELA DE **BOOT**

clover options: 

	configs:
	
		config.plist // Desktops
		config2.plist // Notebooks

		Mac OS Expandido (Journaling)
		Mapa de Partição GUID



### PÓS INSTALAÇÃO

Abrir pasta **Files** e executar:
	
- Master.disable
- Instalar clover

Opções a serem marcadas no Clover:

- Instalar clover na ESP
- Bootloader/Não atualiza os setores de MBR
- CloverEFI/CloverEFI 64-bits SATA
- Instalar o painel de preferências do Clover

Abrir Olarila da pasta Files

Na aba Olarila Folders selecionar Notebooks SkyLake+

### ÁUDIO: 

**Layout IDs:** 5, 11, 13, 14, 21, 22, 28, 56, 57

O layout 11 foi o que funcionou melhor para mim. Consegui com que o microfone funciona-se com ótima qualidade!

Para fazer o audio funcionar é necessário tentar os Layout IDs que estão dispostos e instalar o Kext AppleALC

Também é possível baixar pelo link do Github:
https://github.com/vit9696/AppleALC

Feito isso vá até à config.plist que está na pasta EFI/Clover e em ACPI aplique o patch **change HDAS to HDEF**. 	

Reinicie o Hackintosh e provavelmente estará funcionando. Caso não funcione troque para outro Layout ID e reinicie novamente.


### VÍDEO:

Para certificar-se que o vídeo está funcionando corretamente aplique as seguintes mudanças

Para a intel HD Graphics 520 execute os seguintes procedimentos.
Abra a sua config.plist e selecione a aba lateral esquerda que diz Graphics, e dentro dela marque a caixinha **IntectIntel**

Agora vá até o campo **ig-plataform-id** e selecione **0x19160000** (estará em Skylake mobile)

Por fim coloque **3** no campo **Video Ports**


### TRACKPAD

Para resolver o erro do trackpad execute os seguintes passos:

Usando a kext
ApplePS2SmartTouchPad.kext
Copie o kext para a pasta EFI/Clover/Kext/other/....
Copiar Trackpad.prefPane para /System/Biblioteca/PreferencesPanes.


### TELA INTEGRADA

Usando com o tempo percebi que a qualidade da imagem que chegava a minha tela integrada não era exatamente o que esperava, mesmo com a placa grafica funcionando. Posteriormente adquiri um monitor Full HD da Dell que tentei usar o HDMI e tive sucesso, entretanto o aceleramento gráfico estava meio confuso e estranho. Consegui resolver esse problema aplicando um patch EDID. 

Siga os passos para resolver.

Copie a pastas DisplayVendorID-X e o arquivo Icons.plist para: `/System/Library/Displays/Contents/Resources/Overrides`

Agora, execute o cloverConfigurator e abra sua config.plist. Nela selecione a aba ACPI e aplique o seguinte patch DSDT. 

| 		Comment				 | Find* [HEX] | Replace [HEX] |  
|---------|---------- |----------|
| Rename H_EC to EC__ | 485F4543   | 45435F5F | 





















