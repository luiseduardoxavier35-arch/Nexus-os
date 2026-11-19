# NEXUS Universal Emulator

## Objetivo

Integrar a emulação como uma função de primeira classe do NEXUS OS. O usuário deve encontrar os jogos de PC e de consoles em uma biblioteca única, com detecção de plataforma, configurações centralizadas e inicialização pelo NEXUS Game Center.

"Nativo" significa integrado à experiência, aos serviços e ao ciclo de atualização do NEXUS. Não significa reimplementar os consoles nem incorporar código de terceiros sem respeitar suas licenças.

## Estado da primeira entrega

- Catálogo versionado de plataformas em `/usr/share/nexus/emulation/platforms.json`.
- CLI inicial `nexus-emulator-manager`, com ações `list` e `status`.
- Detecção de executáveis disponíveis no PATH.
- Separação explícita entre plataformas suportadas, experimentais e sem emulador geral maduro.

O MVP atual é somente de inventário/detecção. Ele ainda não instala emuladores, não inicia ROMs e não configura firmware/BIOS.

## Matriz inicial

| Plataforma | Emulador previsto | Estado no NEXUS |
|---|---|---|
| PlayStation 1 | DuckStation | Integração planejada |
| PlayStation 2 | PCSX2 | Integração planejada |
| PlayStation 3 | RPCS3 | Integração planejada |
| PlayStation 4 | shadPS4 | Experimental |
| Xbox clássico | xemu | Integração planejada |
| Xbox 360 | Xenia | Experimental; validar build Linux e compatibilidade |
| Xbox One | — | Sem emulador geral maduro |
| Xbox Series X/S | — | Sem emulador geral maduro |

Os estados acima descrevem o planejamento e a maturidade geral, não uma promessa de compatibilidade de cada jogo. A disponibilidade de pacotes varia por distribuição, arquitetura e versão.

## Arquitetura

1. **Platform Registry** — IDs estáveis, nomes, emulador associado, aliases de executáveis e estado de suporte.
2. **Emulator Manager** — detecção, instalação/atualização por fontes confiáveis e diagnóstico.
3. **Game Scanner** — identifica arquivos e diretórios sem executar conteúdo.
4. **Launch Adapters** — adaptadores específicos por emulador; cada um define argumentos, formato de jogo e validações.
5. **Controller Hub** — mapeamento unificado de controles.
6. **Save Manager** — localização e backup opcional de saves, sem sobrescrever dados silenciosamente.
7. **Compatibility Catalog** — estado por jogo, versão do emulador e observações.
8. **Game Center UI** — biblioteca única e abertura de jogos por adaptador.

## Regras de segurança e legalidade

- Não baixar nem distribuir jogos, BIOS, firmware, chaves ou arquivos proprietários de consoles.
- O usuário deve fornecer dumps e firmware obtidos legalmente e compatíveis com as regras aplicáveis.
- Não executar arquivos importados durante a varredura.
- Mostrar claramente a origem do emulador, licença, versão e método de atualização.
- Não marcar um jogo como compatível apenas porque o emulador abre.
- Não prometer suporte a Xbox One/Series ou compatibilidade universal de PS4.
- Manter os emuladores isolados do restante do sistema sempre que tecnicamente viável.

## Próximas etapas

1. Empacotar o manifesto e o CLI na imagem BlueBuild, com permissões corretas.
2. Adicionar adaptadores de detecção e inicialização por emulador.
3. Implementar importação de jogos e validação de formatos.
4. Criar tela de gerenciamento no NEXUS Game Center.
5. Validar primeiro PS1/PS2 e Xbox clássico; depois PS3, PS4 e Xbox 360 de forma progressiva.
6. Testar no hardware-alvo (Ryzen 5 5600, RX 7600, 16 GB RAM).

## Testes de aceitação do MVP

- O comando lista todas as plataformas sem exigir internet.
- O comando status diferencia emulador detectado, não instalado, experimental e indisponível.
- Manifesto inválido gera erro compreensível.
- Nenhum jogo, BIOS ou firmware é baixado ou executado pelo MVP.
