<p align="center">
  <img src="docs/images/logo.png" alt="ArcMagery" width="170" />
</p>

<h1 align="center">ArcMagery</h1>

<p align="center">
  <strong>Imagens de satélite no ArcGIS Desktop (ArcMap 10.8 / 10.8.2) e no QGIS, direto no mapa e na resolução nativa</strong><br>
  <em>Google Earth Engine · Google Earth (atual e histórico) · Esri Wayback · CBERS-2/2B, CBERS-4/4A e Amazônia-1 (INPE) · SPOT 1–5 (CNES)</em>
</p>

<p align="center">
  <a href="https://github.com/Yiuky/ArcMagery-releases/releases/latest"><img src="https://img.shields.io/github/v/release/Yiuky/ArcMagery-releases?label=Est%C3%A1vel&color=2E8B57" alt="Versão estável"></a>
  <a href="https://github.com/Yiuky/ArcMagery-releases/releases"><img src="https://img.shields.io/github/v/release/Yiuky/ArcMagery-releases?include_prereleases&sort=semver&filter=*-nightly*&label=Nightly&color=E67E22" alt="Versão experimental (nightly)"></a>
  <a href="https://github.com/Yiuky/ArcMagery-releases/releases"><img src="https://img.shields.io/github/downloads/Yiuky/ArcMagery-releases/total?label=Downloads&color=555" alt="Downloads"></a>
  <a href="https://www.esri.com/"><img src="https://img.shields.io/badge/ArcGIS%20Desktop-10.8%20%7C%2010.8.2-0079C1.svg?logo=esri&logoColor=white" alt="ArcGIS Desktop"></a>
  <a href="https://qgis.org/"><img src="https://img.shields.io/badge/QGIS-3.18%2B-589632.svg?logo=qgis&logoColor=white" alt="QGIS 3.18+"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/Licen%C3%A7a-Propriet%C3%A1ria%20(uso%20gratuito)-blue.svg" alt="Licença proprietária, uso gratuito"></a>
</p>

<p align="center">
  <a href="https://github.com/Yiuky/ArcMagery-releases/releases/latest"><strong>⬇️ Baixar</strong></a> •
  <a href="docs/MANUAL_DE_USO_E_INSTALACAO.md"><strong>📖 Manual</strong></a> •
  <a href="docs/QMAGERY.md"><strong>🧩 QGIS (QMagery)</strong></a> •
  <a href="https://github.com/Yiuky/ArcMagery-releases/releases"><strong>📋 Novidades</strong></a> •
  <a href="https://github.com/Yiuky/ArcMagery-releases/issues/new/choose"><strong>🐞 Relatar problema</strong></a> •
  <a href="#-english-abstract"><strong>🌐 English</strong></a> •
  <a href="#-doe-um-café-para-o-dev"><strong>☕ Doe um café</strong></a>
</p>

---

<p align="center">
  <img src="docs/images/janela_principal.png" alt="Janela principal do ArcMagery" width="94%" />
</p>

## 📌 O que é

O **ArcMagery** é um Add-In para o **ArcMap 10.8/10.8.2** que busca, recorta e carrega imagens de satélite
direto no TOC, na **resolução nativa**, sem sair do ArcMap e sem downloads manuais. O **QMagery** é o mesmo
ArcMagery no **QGIS 3.18+**. Os dois servem a quem trabalha com sensoriamento remoto, monitoramento ambiental
e perícias.

> Projeto **pessoal e independente** de Joberth Firmino Gambati: não é um produto oficial de nenhuma instituição
> nem fala em nome dela. Este repositório distribui os **pacotes, o manual e as atualizações**; o código-fonte é
> mantido em repositório privado.

## 🗺️ Fontes de imagens

| Fonte | O que oferece | Resolução |
|---|---|---|
| **Google Earth Engine** | Sentinel-2, Landsat 1–9: cenas, mosaicos por mediana com máscara de nuvem, índices (NDVI, NDWI, NDMI, NBR, EVI, SAVI), matemática de bandas e multibanda completa | 10–60 m |
| **CBERS / Amazônia-1 (INPE)** | STAC do INPE, 32 coleções: CBERS-4A WPM (2 m pan, 8 m multiespectral, fusionada 2 m), MUX, WFI, PAN 5/10 m, Amazônia-1 WFI; cubos sem nuvens com NDVI/EVI; histórico CBERS-2/2B (2003–2010) | 2–260 m |
| **SPOT 1–5 (CNES)** | Acervo SPOT World Heritage 1986–2015 pelo GEODES, com **alinhamento automático à Esri** (o produto bruto vem com 150–480 m de erro; depois, ~2–5 m). Busca livre; download com a chave gratuita do GEODES | 2,5–20 m |
| **Google Earth histórico** | As datas do histórico do Google Earth (como no Google Earth Pro), com provedor e cobertura | ~0,15–4,8 m |
| **Esri Wayback** | Versões da Esri World Imagery desde 2014, com a **data de captura**, o satélite e a resolução | ~0,3–4,6 m |
| **Google Earth / XYZ** | Google Satélite e Híbrido, Esri World Imagery e Clarity, Bing Aerial, costurados num GeoTIFF georreferenciado | até ~0,15 m |

### Destaques
- **Qualidade nativa:** Earth Engine sem reamostragem involuntária; CBERS recortado na grade original da cena
  (só a área de interesse é transferida); SPOT na resolução do sensor, em UTM SIRGAS 2000.
- **Áreas extensas:** particionamento automático, com cache e retomada após falhas.
- **Área de interesse:** extensão atual do mapa ou camada vetorial do TOC; CBERS e SPOT mostram quanto da área
  cada cena **realmente** cobre.
- **Sem travar o ArcMap:** a janela roda em processo próprio; downloads longos não bloqueiam o mapa.
- **Simbologia conferida:** bandas RGB e realce aplicados e verificados em cada camada carregada.
- **Rede corporativa:** certificados do Windows em todas as conexões (proxy com inspeção SSL), sempre com
  verificação do certificado.

---

## 💻 Requisitos

| Item | ArcMagery (ArcMap) | QMagery (QGIS) |
|---|---|---|
| Windows | 10 ou 11, 64 bits | 10 ou 11, 64 bits |
| Programa | ArcGIS Desktop **10.8 / 10.8.2** (ArcMap) | QGIS **3.18 ou mais novo** |
| Python, GDAL, numpy | **Já embutidos** no motor do ArcMagery (~90 MB, baixado na instalação). Não é preciso QGIS nem `pip` | Os do próprio QGIS |
| Administrador | Não precisa | Não precisa |
| Google Earth Engine | Conta com projeto do Google Cloud (só para essa fonte) | Idem |
| SPOT | Chave gratuita do [GEODES](https://geodes-portal.cnes.fr) (só para **baixar**; a busca é livre) | Idem |

## 📦 Arquivos de cada versão

Em cada [Release](https://github.com/Yiuky/ArcMagery-releases/releases):

| Arquivo | Para que serve | Precisa baixar? |
|---|---|---|
| `ArcMagery-<versão>.zip` | Add-In do ArcMap, com o `install.bat` | **Sim** (ArcMap) |
| `QMagery-<versão>.zip` | Plugin do QGIS | Só se não usar o repositório de plugins |
| `ArcMagery-Engine-<versão>-win64.zip` (+ `.sha256`) | Motor do ArcMagery (Python 3 + GDAL) | **Não**: o `install.bat` baixa e confere sozinho. Baixe só para instalar sem internet |
| `SHA256SUMS.txt` | Hashes SHA-256 dos pacotes | Para conferir a integridade |

**Estável** é a versão recomendada. **Nightly** (`X.Y.Z-nightly.AAAAMMDD`, marcada como *pre-release*) recebe as
novidades antes, para quem quer testar.

## ⚡ Instalação no ArcMap

1. Baixe o `ArcMagery-<versão>.zip` da [última Release](https://github.com/Yiuky/ArcMagery-releases/releases/latest).
   Antes de extrair, abra as *Propriedades* do ZIP e marque **Desbloquear** (evita o aviso do Windows).
2. Extraia numa **pasta de caminho curto** (ex.: `C:\ArcMagery`).
3. Feche o ArcMap e dê um duplo clique em **`install.bat`**. O instalador:
   - baixa e confere (SHA-256) o **motor** do ArcMagery (~90 MB);
   - roda o **diagnóstico**, que corrige o que é seguro e diz *o que fazer* no resto
     (relatório em `%LOCALAPPDATA%\ArcMagery\diagnostico.txt`);
   - instala e registra o Add-In.
4. No ArcMap: **Customize › Toolbars › ArcMagery** e clique no botão **ArcMagery**.
5. Para o Earth Engine, na janela: **Configurar Projeto GEE › Entrar com o Google** e escolha o projeto.

Passo a passo completo, instalação manual e sem internet: [manual, seção 4](docs/MANUAL_DE_USO_E_INSTALACAO.md#4-instalação).

## 🧩 Instalação no QGIS (QMagery)

1. No QGIS: **Complementos › Gerenciar e instalar complementos › Configurações**.
2. Em *Repositórios de complementos*, clique em **Adicionar...** e informe:
   - **Nome:** `ArcMagery`
   - **URL:** `https://raw.githubusercontent.com/Yiuky/ArcMagery-releases/main/qgis_plugin/plugins.xml`
3. Na aba **Todos**, procure **QMagery** e clique em **Instalar complemento**. O QGIS passa a avisar as atualizações.

Para receber também as nightlies, marque *Mostrar também os complementos experimentais*. Sem o repositório:
*Instalar a partir do ZIP* com o `QMagery-<versão>.zip`. Manual: [docs/QMAGERY.md](docs/QMAGERY.md).

## 🔄 Atualizar e voltar de versão

- O ArcMagery avisa quando há versão nova: **Sim** já atualiza (pacote conferido por SHA-256, com backup antes).
- **⚙ Configurações › Assistente de Atualização:** canal *Estável* ou *Experimental*, instalação a partir de um
  ZIP e **Voltar para a versão anterior** (rollback com um clique).
- Sem o assistente: baixe a nova Release e rode o `install.bat` dela.

## 🔐 Conferir a integridade

Os pacotes são conferidos automaticamente pelo instalador e pelo atualizador. Para conferir à mão, no PowerShell:

```powershell
Get-FileHash .\ArcMagery-*.zip -Algorithm SHA256
```

O resultado deve ser igual à linha do arquivo no `SHA256SUMS.txt` da mesma Release.

## 🆘 Problemas comuns

| Mensagem | O que fazer |
|---|---|
| **"Extensão ArcMap Indefinida"** | Feche janelas abertas do ArcMap (ex.: *Propriedades do Data Frame*), confirme que o mapa tem uma camada com dados e sistema de coordenadas definido. Ao carregar, o ArcMagery oferece a área da última busca. Alternativa: **Camada Vetorial (AOI)**. [Manual](docs/MANUAL_DE_USO_E_INSTALACAO.md#861-extensão-arcmap-indefinida) |
| **Erro de certificado** (`CERTIFICATE_VERIFY_FAILED`, *self-signed certificate*) | A rede, o antivírus ou o proxy está trocando o certificado HTTPS. Peça ao TI para instalar o certificado raiz no Windows, ou aponte a variável `ARCMAGERY_CA_BUNDLE` para o `.pem` dele. [Manual](docs/MANUAL_DE_USO_E_INSTALACAO.md#891-erro-de-certificado-certificate_verify_failed-self-signed-certificate-in-certificate-chain) |
| **O motor não foi instalado** | Verifique internet/proxy e rode o `install.bat` de novo. Sem acesso ao GitHub: instalação offline do motor. [Manual](docs/MANUAL_DE_USO_E_INSTALACAO.md#82-o-motor-não-foi-instalado-sem-internet-ou-github-bloqueado) |
| **"O Windows protegeu o computador"** ao abrir o `.bat` | *Mais informações › Executar assim mesmo*, ou desbloqueie o ZIP antes de extrair |
| **Earth Engine: sem permissão no projeto** | Use **Configurar Projeto GEE** e escolha um projeto registrado no Earth Engine (a janela tem o tutorial). Um projeto com erro nunca substitui o que já funcionava |
| **SPOT: "GEODES recusou a chave"** | Copie de novo a chave inteira do campo *API Key* no portal do GEODES |

Lista completa: [manual, seção 8](docs/MANUAL_DE_USO_E_INSTALACAO.md#8-solução-de-problemas). Se não resolver,
[abra uma issue](https://github.com/Yiuky/ArcMagery-releases/issues/new/choose) com a versão (botão **ℹ Sobre**), a
mensagem e o `diagnostico.txt`.

> ⚠️ **Termos de uso das fontes:** o download em massa de tiles do **Google** (inclusive o histórico), do **Bing**
> e da **Esri** fora das APIs oficiais pode violar os termos desses serviços (para Google e Bing, o ArcMagery avisa
> antes do primeiro uso). Para dados abertos, prefira **CBERS/INPE**, **SPOT/CNES** (Etalab 2.0; cite *"SPOT images
> acquired by CNES's Spot World Heritage Programme"*) e o **Earth Engine**, conforme a licença de cada coleção.

## 🛡️ Privacidade e segurança

- Tudo é instalado no **perfil do usuário**, sem administrador. O login do Google e a chave do GEODES ficam só
  neste computador e só são enviados ao próprio provedor.
- Atualizações conferidas por SHA-256, com backup e restauração automática se algo falhar.
- Vulnerabilidades: siga a [política de segurança](SECURITY.md) (não abra issue pública).
- Endereços acessados e pastas usadas: [manual, seção 9](docs/MANUAL_DE_USO_E_INSTALACAO.md#9-dados-guardados-no-computador-e-rede).

## 📝 Como citar

O uso é gratuito e a **citação é obrigatória** em trabalhos acadêmicos, técnicos, institucionais, periciais ou
corporativos. Use o botão **Cite this repository** do GitHub (gerado a partir do [CITATION.cff](CITATION.cff)) ou:

```bibtex
@software{gambati_arcmagery,
  author = {Gambati, Joberth Firmino},
  title  = {ArcMagery: imagens de satélite no ArcMap e no QGIS na resolução nativa},
  url    = {https://github.com/Yiuky/ArcMagery-releases}
}
```

---

## 🌐 English Abstract

**ArcMagery** is an independent, personal Add-In (free to use; citation required) for **ArcGIS Desktop 10.8 /
10.8.2 (ArcMap)** that searches, clips and loads satellite imagery straight into the table of contents, at native
resolution; **QMagery** brings the same tool to **QGIS 3.18+**. Sources: **Google Earth Engine** (Sentinel-2,
Landsat 1–9, cloud-masked mosaics, spectral indices, band math), **CBERS-4/4A and Amazonia-1** (INPE STAC, clipped
on the native grid), **SPOT 1–5** (CNES SPOT World Heritage 1986–2015, automatically co-registered to Esri World
Imagery), **Google Earth historical imagery**, **Esri Wayback** and **XYZ basemaps**.

Install: download `ArcMagery-<version>.zip` from the [latest release](https://github.com/Yiuky/ArcMagery-releases/releases/latest)
and run `install.bat` (no admin rights, no QGIS and no `pip` needed: a compiled engine with Python 3 and GDAL is
downloaded and SHA-256 verified). For QGIS, add the plugin repository
`https://raw.githubusercontent.com/Yiuky/ArcMagery-releases/main/qgis_plugin/plugins.xml`. Works behind
TLS-inspecting proxies (Windows certificate store; `ARCMAGERY_CA_BUNDLE` for a custom root). Stable and nightly
channels, SHA-256 verified updates and one-click rollback. The user manual is in Portuguese.

## ☕ Doe um café para o dev

O ArcMagery é gratuito, desenvolvido nas horas vagas. Se ele economizou o seu tempo, considere pagar um café para o
desenvolvedor: ajuda a manter o projeto vivo e a trazer novas fontes de imagem.

<table>
  <tr>
    <td align="center"><img src="docs/images/pix_qrcode.png" alt="QR Code Pix" width="180" /></td>
    <td>
      <strong>Pix</strong> (qualquer valor)<br><br>
      Chave aleatória:<br>
      <code>fcf8071f-416d-49f1-b4b9-3188d3d03c4b</code><br><br>
      Pix copia e cola:<br>
      <code>00020101021126580014br.gov.bcb.pix0136fcf8071f-416d-49f1-b4b9-3188d3d03c4b5204000053039865802BR5917JOBERTH F GAMBATI6006CUIABA62070503***63048088</code><br><br>
      <em>Favorecido: Joberth Firmino Gambati</em>
    </td>
  </tr>
</table>

## 👤 Autor e licença

- **Desenvolvedor:** Joberth Firmino Gambati ([@Yiuky](https://github.com/Yiuky)).
- **Licença:** [proprietária, de uso gratuito](LICENSE) ([NOTICE](NOTICE)): citação obrigatória; redistribuição e
  engenharia reversa dependem de autorização. Código-fonte, parcerias e uso comercial: contato direto com o autor.
  As versões até a 2.4.3 foram publicadas sob a MIT.
- **Componentes de terceiros:** [docs/THIRD_PARTY_NOTICES.txt](docs/THIRD_PARTY_NOTICES.txt).
- **Imagens:** © Google, © Esri e parceiros, © Microsoft, CBERS/Amazônia-1 © INPE, SPOT © CNES (Etalab 2.0) e os
  provedores do Google Earth Engine. Respeite a licença de cada fonte.
