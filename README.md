# ArcMagery: Binários e Atualizações

Repositório oficial de distribuição de binários, instaladores e atualizações do **ArcMagery** (Add-In para ArcGIS Desktop / ArcMap 10.8) e do **QMagery** (Plugin para QGIS 3.18+).

> Projeto **pessoal e independente** de Joberth Firmino Gambati.

---

## 🛰️ O que é o ArcMagery?

O **ArcMagery** integra o download e processamento de imagens de satélite em resolução nativa diretamente no software SIG:
- **Google Earth Engine (GEE):** Sentinel-2 (L2A, L1C), Landsat 1-9 (SR/TOA).
- **INPE (STAC):** CBERS-4/4A (WPM, MUX, AWFI) e Amazônia-1 (WFI) com recorte remoto `/vsicurl/`.
- **CNES / GEODES:** SPOT 1-5 com ortorretificação e alinhamento automático à Esri World Imagery.
- **Google Earth Histórico:** Mosaicos históricos por data de passagem via protocolo Keyhole.
- **Esri World Imagery Wayback:** Mosaicos históricos de alta resolução temporal.
- **Mosaicos XYZ:** Google Earth, Esri, Bing e provedores personalizados.

---

## 📥 Como Instalar

### ArcMap 10.8 / 10.8.2 (ArcMagery)
1. Acesse a aba **[Releases](https://github.com/Yiuky/ArcMagery-releases/releases/latest)** deste repositório.
2. Baixe o pacote `ArcMagery-<versão>.zip` ou o instalador automatizado.
3. Extraia o conteúdo e execute `install.bat`.
4. Abra o ArcMap e ative a barra de ferramentas do ArcMagery.

### QGIS 3.18+ (QMagery)
1. No QGIS, acesse **Complementos** › **Gerenciar e Instalar Complementos...** › **Configurações**.
2. Marque a opção *"Mostrar também os complementos experimentais"*.
3. Em *Repositórios de Complementos*, clique em **Adicionar...** e insira:
   - **Nome:** `QMagery Plugins`
   - **URL:** `https://raw.githubusercontent.com/Yiuky/ArcMagery-releases/main/qgis_plugin/plugins.xml`
4. Vá para a aba *Todos*, procure por **QMagery** e clique em **Instalar complemento**.

Alternativamente, baixe o arquivo `QMagery-<versão>.zip` na aba **Releases** e utilize a opção *Instalar a partir do ZIP*.

---

## 📦 Motor Autônomo (ArcMagery Engine)

Para usuários que não possuem o QGIS instalado como backend Python, disponibilizamos nas Releases o **ArcMagery Engine** compilado (`ArcMagery-Engine-<versão>-win64.zip`), contendo GDAL, PROJ e todas as dependências pré-configuradas.

---

## 📜 Licença, Autoria e Citação Obrigatória

O ArcMagery é disponibilizado sob termos de uso que exigem atribuição estrita. **Qualquer uso acadêmico, técnico, institucional, pericial ou corporativo deve obrigatoriamente citar o ArcMagery e seu autor.**

Consulte o arquivo [LICENSE](LICENSE) e o arquivo [CITATION.cff](CITATION.cff) para o formato exato de citação:

```bibtex
@software{gambati_arcmagery,
  author = {Gambati, Joberth Firmino},
  title = {ArcMagery: imagens de satélite no ArcMap e QGIS na resolução nativa},
  url = {https://github.com/Yiuky/ArcMagery-releases}
}
```

---

## 🔒 Acesso ao Código-Fonte

O código-fonte do motor e dos plugins é mantido em repositório privado. Para colaborações acadêmicas, parcerias ou auditoria técnica do código-fonte, entre em contato com o autor via GitHub Issues ou pelo e-mail institucional/pessoal informado nos metadados.
