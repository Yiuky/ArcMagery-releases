# Política de segurança

## Versões com correções

| Versão | Recebe correções de segurança |
|---|---|
| 2.4.x (estável mais recente) | Sim |
| Experimental (`-nightly`) | Sim, na próxima versão experimental |
| Anteriores a 2.4 | Não: atualize pelo Assistente de Atualização |

## Como relatar uma vulnerabilidade

**Não abra uma issue pública.** Use o relato privado do GitHub:
[Report a vulnerability](https://github.com/Yiuky/ArcMagery-releases/security/advisories/new)
(aba *Security* do repositório).

Inclua a versão afetada, os passos para reproduzir e o impacto esperado. A resposta inicial costuma sair em
até 7 dias; por ser um projeto mantido nas horas vagas, a correção pode levar mais tempo, e você será
informado do andamento.

## O que já é protegido

- **Atualizações:** pacotes da Release conferidos por SHA-256; ZIPs verificados contra caminhos maliciosos
  (*path traversal*) antes de extrair; backup antes de cada mudança, com restauração automática se algo
  falhar.
- **Dependências do Earth Engine:** instaladas de *wheels* com versão fixa e hash SHA-256 conferido.
- **Credenciais:** a chave do GEODES e o login do Earth Engine ficam só no perfil do usuário do
  Windows e nunca são enviados a outro serviço além do próprio provedor.
