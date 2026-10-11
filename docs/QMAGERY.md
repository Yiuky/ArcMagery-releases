# QMagery — manual do plugin para o QGIS

O **QMagery** leva para o **QGIS 3.18 ou mais novo** as mesmas fontes de imagens do ArcMagery, com o mesmo
backend: busca as cenas da área, recorta na resolução nativa e carrega no painel de camadas.

| Fonte | O que oferece |
|---|---|
| **Google Earth Engine** | Sentinel-2 e Landsat 1–9: composições, multibanda, índices (NDVI, NDWI, NDMI, NBR, EVI, SAVI), bandas e fórmulas digitadas |
| **CBERS / Amazônia-1 (INPE)** | As 32 coleções do STAC do INPE (CBERS-2/2B/4/4A, Amazônia-1, cubos e mosaicos) |
| **SPOT 1–5 (CNES)** | Acervo 1986–2015 pelo GEODES, alinhado automaticamente à Esri World Imagery |
| **Google Earth histórico** | As datas do histórico na área, uma camada por data |
| **Esri Wayback** | As versões da Esri World Imagery, com a data de captura |
| **Google Earth / XYZ** | Google, Esri e Bing como camada XYZ ao vivo ou como GeoTIFF da área |

> **Estável desde a 2.4.3.** As novidades saem antes como *nightly* (experimentais), para quem marcar
> *Mostrar também os complementos experimentais*. Projeto pessoal e independente, de uso gratuito sob licença proprietária (citação obrigatória).

## 1. Instalar

### Recomendado: pelo repositório de plugins (recebe as atualizações sozinho)

1. No QGIS: **Complementos › Gerenciar e instalar complementos › Configurações**.
2. Opcional: marque **Mostrar também os complementos experimentais** para receber também as nightlies.
3. Em **Repositórios de complementos**, clique em **Adicionar...** e preencha:
   - Nome: `QMagery`
   - URL: `https://raw.githubusercontent.com/Yiuky/ArcMagery-releases/main/qgis_plugin/plugins.xml`
4. Clique em **Recarregar todos os repositórios**, procure **QMagery** em **Todos** e clique em **Instalar**.

O botão **QMagery** aparece na barra de ferramentas e no menu **Raster › QMagery**.

### Alternativa: a partir do ZIP

1. Baixe o `QMagery-<versão>.zip` da [última Release](https://github.com/Yiuky/ArcMagery-releases/releases)
   (confira o hash em `SHA256SUMS.txt`, se quiser).
2. No QGIS: **Complementos › Gerenciar e instalar complementos › Instalar a partir do ZIP**, escolha o
   arquivo e clique em **Instalar complemento**.

Instalado pelo ZIP, o QGIS não avisa as atualizações: cadastre o repositório acima para recebê-las.

## 2. Atualizar e voltar de versão

- Com o repositório cadastrado, o QGIS avisa na barra de status e na aba **Atualizáveis** do Gerenciador
  de Complementos. Clique em **Atualizar complemento**.
- Nightly × estável: o QGIS só oferece as versões experimentais com a opção **Mostrar também os
  complementos experimentais** marcada. Desmarcada, fica só nas estáveis.
- Para voltar a uma versão anterior, instale o `QMagery-<versão>.zip` dela pelo **Instalar a partir do ZIP**.
- As configurações (projeto do GEE, chave do GEODES, pasta de saída) ficam fora da pasta do plugin e
  sobrevivem às atualizações.

As versões nightly aparecem no QGIS como `X.Y.Z-beta.AAAAMMDD` (a mesma `vX.Y.Z-nightly.AAAAMMDD` da
Release): é a forma que o QGIS entende como anterior à `X.Y.Z` estável.

## 3. Primeira abertura

Ao abrir, a **verificação do ambiente** confere o Python do QGIS, o GDAL, o numpy, os componentes do Earth
Engine, a internet (INPE, GEODES, Esri) e a chave do GEODES. Nada ali impede o uso: as fontes que não
dependem do item com aviso continuam funcionando.

- **Componentes do Earth Engine ausentes:** clique em **Instalar componentes do Earth Engine** (cerca de
  25 MB, sem `pip`, com os certificados do Windows; funciona atrás de proxy com inspeção SSL).
- A verificação pode ser desligada em **⚙ Configurações** e rodada a qualquer momento em
  **Raster › QMagery › Verificar o ambiente...**.

### Google Earth Engine (só para a fonte GEE)

1. Clique em **Projeto GEE...**, informe o ID do projeto do Google Cloud com a Earth Engine API habilitada.
2. Clique em **Autenticar no Google...**: um console abre e, em seguida, o navegador. Entre com a conta que
   tem acesso ao Earth Engine. Quando o console fechar, o QMagery verifica a conexão.

### SPOT (só para baixar; a busca é livre)

Em **⚙ Configurações › Chave do GEODES (SPOT)...**, siga os passos, cole a chave e clique em
**Testar chave** (mostra a cota: 50 cenas por hora). Cenas já baixadas ficam em cache e não gastam cota.

> O ArcMagery e o QMagery usam os **mesmos arquivos** de configuração (`%APPDATA%\ArcGEE\gee_config.json` e
> `geodes_config.json`): configurou num, vale no outro.

## 4. Usar

1. Escolha a **fonte** na barra azul e o **satélite/sensor** (no Google Earth histórico e no Wayback, o
   zoom ocupa o lugar do sensor).
2. Escolha a **composição** (no GEE, as composições de cada satélite; **bandas personalizadas** e
   **fórmula** abrem o campo de texto), o **período** e a **área de interesse**:
   - **Extensão da tela**: até a escala 1:500.000 (o QMagery oferece ajustar o zoom);
   - **Camada vetorial**: uma camada de polígonos do projeto (só as feições selecionadas, se houver),
     em qualquer sistema de coordenadas.
3. Clique em **Buscar**. Cada linha da tabela é uma cena (ou uma data/versão).
4. Selecione uma ou várias linhas (Ctrl/Shift) e clique em **Carregar no QGIS**: cada cena vira uma
   camada, baixadas em fila. Duplo clique numa linha mostra a **miniatura**.
5. **Substituir camada**: escolha a camada raster em *Camada a substituir* e clique em **Substituir
   camada**; a nova ocupa o mesmo grupo e a mesma posição.

As camadas entram com a simbologia certa: multibanda do GEE em cor natural, índices com rampa de cores,
SPOT e CBERS conforme a composição. Os GeoTIFFs ficam em **Documentos\QMagery** (uma subpasta por
fonte; mude em **⚙ Configurações**) e continuam no projeto depois de reiniciar o QGIS.

**Interromper** cancela a operação atual e o restante da fila. Fechar a janela durante um download pede
confirmação.

### Google Earth / XYZ

O botão **Google Earth / XYZ...** abre os mosaicos (Google, Esri, Bing):

- **Adicionar como camada XYZ**: camada ao vivo, sem download (Bing só como download);
- **Baixar GeoTIFF da área**: costura os tiles da área de interesse no zoom escolhido;
- **Estimar**: número de tiles, tamanho e volume antes de baixar.

> ⚠️ **Termos de uso:** Google e Bing não liberam o download em massa de tiles; use essas imagens só para
> consulta e visualização, e cite a fonte. A Esri tem termos próprios. Para dados abertos, prefira
> CBERS (INPE), SPOT (CNES, Etalab 2.0) ou o Earth Engine.

## 5. Solução de problemas

| Sintoma | O que fazer |
|---|---|
| "Backend não encontrado" | Reinstale o QMagery pelo repositório ou pelo ZIP da Release (o código-fonte do GitHub não é um pacote instalável). |
| Earth Engine: "componentes não instalados" | Abra **Verificar o ambiente** e clique em **Instalar componentes do Earth Engine**. |
| Earth Engine: "autentique-se" ou "informe o projeto" | **Projeto GEE...** › informe o projeto › **Autenticar no Google...**. |
| SPOT: pede a chave | **⚙ Configurações › Chave do GEODES (SPOT)...**; a chave gratuita sai em 3 minutos. |
| "A área exige mais de 120 partes" (GEE) | Aproxime o mapa, use uma camada vetorial menor ou aumente o tamanho do pixel. |
| "O backend ficou N s sem responder" | Rede instável ou área grande: tente de novo ou reduza a área. |
| Internet bloqueada na verificação | Confira proxy/firewall; o QMagery usa os certificados do Windows. |

Se o problema continuar, [abra uma issue](https://github.com/Yiuky/ArcMagery-releases/issues/new/choose) com a
versão (botão **ℹ Sobre**), o texto do erro e o que estava fazendo.

## 6. Desinstalar

**Complementos › Gerenciar e instalar complementos › Instalados › QMagery › Desinstalar complemento.**
As configurações compartilhadas com o ArcMagery ficam em `%APPDATA%\ArcGEE` (apague a pasta se não usar
nenhum dos dois); os GeoTIFFs, em Documentos\QMagery.

