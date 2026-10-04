# Validação no Windows

Use mídia de teste sem dados sensíveis. Não publique logs sem remover nome de usuário, caminhos pessoais e tokens.

## Ambiente

- [ ] Codex instalado e aberto.
- [ ] Python 3.10 ou superior, Node.js 22 ou superior, ffmpeg e ffprobe disponíveis.
- [ ] A skill está em `%USERPROFILE%\.codex\skills\video-edit` e contém `SKILL.md`.

## Verificação sem alterações

No PowerShell:

```powershell
python "$HOME\.codex\skills\video-edit\scripts\setup.py" --check
```

- [ ] O comando apenas verifica e não instala ou baixa arquivos.
- [ ] Dependências ausentes são informadas sem execução automática.

## Instalação autorizada

Após revisar pacotes e origens:

```powershell
python "$HOME\.codex\skills\video-edit\scripts\setup.py" --install
python "$HOME\.codex\skills\video-edit\tests\test_platform.py"
```

- [ ] `.platform.json` aponta para caminhos válidos em `.codex`.
- [ ] Nenhum token ou segredo aparece no arquivo.

## Teste funcional

No Codex, use:

```text
Use $video-edit para criar um teste de até 10 segundos com este clipe específico: C:\caminho\teste.mp4.
Salve em C:\caminho\saida. Não use rede, mídia externa nem inserts.
```

- [ ] O Codex confirma o arquivo e o destino antes de processar.
- [ ] O original permanece inalterado.
- [ ] Textos, legendas e relatório usam português do Brasil.
- [ ] O render respeita área segura e sincronização.
- [ ] A entrega fica local e não é publicada.

Se ocorrer uma falha, compartilhe somente o erro necessário e remova informações pessoais antes de abrir uma issue.
