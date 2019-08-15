# Samsung Hackintosh

Modelo: NP300E5L

Resumo:

Quase todo o sistema está em pleno funcionamento.

Itens que não foi possível configurar:

- Wireless Qualcomm Atheros QCA9377



### Audio: 

**Layout IDs:** 5, 11, 13, 14, 21, 22, 28, 56, 57

Para fazer o audio funcionar é necessário tentar os Layout IDs que estão dispostos e instalar o Kext AppleALC

Também é possível baixar pelo link do Github:
https://github.com/vit9696/AppleALC

Feito isso vá até à config.plist que está na pasta EFI/Clover e em ACPI aplique o patch **change HDAS to HDEF**. 	

Reinicie o Hackintosh e provavelmente estará funcionando. Caso não funcione troque para outro Layout ID e reinicie novamente.


### Vídeo:

Para certificar-se que o vídeo está funcionando corretamente aplique as seguintes mudanças

Para a intel HD Graphics 520 execute os seguintes procedimentos.
Abra a sua config.plist e selecione a aba lateral esquerda que diz Graphics, e marque a caixinha **IntectIntel**

Agora vá até o campo **ig-plataform-id** e selecione **0x191b0000** (estará em Skylake mobile)



