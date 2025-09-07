# Ajuda

Um guia para instalação e execução de software. Encontre soluções para problemas comuns, instruções de atualização, configuração e dicas para o uso de funcionalildades.

## Fontes

<details>
<summary>O que são fontes</summary>

Fontes são canais de distribuição de software que podem ser remotas ou locais, usadas para instalação e atualização.

Permitir a seleção entre fontes é uma estratégia flexível que aumenta a disponibilidade do software, dando aos usuários a opção entre atualização automática e controle local. O recurso atende a cenários de desenvolvimento, produção e emergência e possibilita estratégias híbridas, combinando automação com segurança e redundância para rollback.

</details>

<details>
<summary>Escolher uma fonte</summary>

Ambas as abordagens oferecem vantagens, e a escolha depende da prioridade entre o controle, velocidade e disponibilidade.

- Fonte remota
    - Atualizações imediatas. Releases são obtidas assim que publicadas no repositório oficial;
    - Distribuição global. GitHub e CDNs reduzem latência para usuários geograficamente dispersos;
    - Ideal para usuários que querem sempre a versão mais recente ou integração contínua.
- Fonte local
    - Funciona offline. Instalações e atualizações sem dependência de rede;
    - Controle total sobre o software. Útil para builds internos, testes e versões customizadas;
    - Maior previsibilidade em ambientes isolados ou corporativos;
    - Rapidez em reinstalações repetidas, sem consumo de banda externa;
    - Facilita rollback imediato ao manter cópias locais de versões anteriores;
    - Reduz riscos de disponibilidade por rate limits ou falhas no repositório remoto;
    - Ideal para air-gapped, QA, ou quando é necessário auditar cada artefato manualmente.

</details>

<details>
<summary>Locais das fontes</summary>

- Fonte remota: repositório oficial do projeto no **GitHub**.
- Fonte local: diretório **Downloads** do usuário local.

> A fonte remota acessa diretamente os arquivos publicados no GitHub, enquanto a fonte local utiliza arquivos previamente baixados para o diretório Downloads do usuário local.

</details>

<details>
<summary>Provisionar uma fonte local</summary>

Provisionar uma fonte local significa preparar os arquivos de instalação ou atualização para que possam ser usados a partir da rede local. O processo consiste em obter os pacotes desejados, armazená-los no local apropriado e garantir que estejam íntegros e prontos para uso.

- **Obter:** Baixe os **pacotes** de software e o arquivo **Metadata.json** a partir do repositório oficial ou gere uma release interna.
- **Armazenar:** Copie ou mova os arquivos para o diretório **Downloads** do usuário local, que é o caminho padrão usado para a fonte local.
- **Validar:** Verifique o hash dos pacotes de software para garantir que não foram corrompidos ou alterados.
- **Configurar:** No software, ajuste a configuração para usar a fonte local como origem de instalação ou atualização. Em ambientes híbridos, é possível alternar entre fonte remota e local conforme necessário.
- **Testar:** Execute uma instalação ou atualização de teste para validar que o software está reconhecendo a fonte local e utilizando os arquivos adequadamente.

> Mantenha o nome dos arquivos conforme disponibilizado no repositório oficial, para evitar falhas de reconhecimento.

</details>

## Instalação

<details>
<summary>Como instalar</summary>

- Windows
    - Baixe e descomprima o pacote;
    - Abra o PowerShell;
    - Habilite a execução de scripts `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force`;
    - Desbloqueie o script `Get-Item Workflow.ps1 | Unblock-File`;
    - Execute `.\Workflow.ps1`.
- Linux
    - Baixe e descomprima o pacote;
    - Abra o PowerShell `pwsh`;
    - Execute `./Workflow.ps1`.

> Ao executar o software pela primeira vez, você precisará escolher uma fonte de instalação. Prefira a fonte **Remota**. Caso opte pela fonte local, verifique como provisionar uma fonte local.
    
</details>

<details>
<summary>Como executar</summary>

- Windows
    - Abra o PowerShell;
    - Navegue até a pasta inicial `Set-Location $Home`;
    - Execute `.\Workflow.ps1`.
- Linux
    - Abra o PowerShell `pwsh`;
    - Navegue até a pasta inicial `Set-Location $Home`;
    - Execute `./Workflow.ps1`.

> Após a instalação, você pode usar o atalho criado no diretório do usuário local para executar o software.

</details>

<details>
<summary>O software não é instalado automaticamente</summary>

Você está executando uma versão de software sem suporte. Utilize a versão mais recente para prosseguir. Verifique [Evolução][Evolução] e [Política de Suporte][Política de Suporte] para mais informações.

</details>

<details>
<summary>Atalho ausente no diretório do usuário</summary>

Se o atalho `Workflow.ps1` estiver ausente no diretório `$Home` após a instalação, verifique o tópico **Acesso a Pastas Controladas** na seção **Software de Terceiros**. Em seguida execute Workflow manualmente a partir do diretório de instalação de software. O atalho será recriado automaticamente. Verifique a seção **Estrutura** para mais informações.

</details>

<details>
<summary>Notificação de incompatibilidade ao instalar</summary>

O software verifica diversas informações do ambiente para garantir que seja executado em um cenário mínimo de compatibilidade. Verifique os requisitos de sistema na página de download e tente novamente após resolver a incompatibilidade.

</details>

<details>
<summary>Como desinstalar</summary>

Siga para `Configurações` `>` `Desinstalar`.

</details>

## Atualização

<details>
<summary>Como manter o software atualizado</summary>

Prossiga conforme a fonte configurada:

- Fonte remota
    - Mantenha-se online;
    - Habilite a atualização automática;
    - Execute o software regularmente.
- Fonte local
    - Mantenha a fonte local provisionada e atualizada adequadamente;
    - Habilite a atualização automática;
    - Execute o software regularmente.

</details>

<details>
<summary>O software não recebe atualizações automaticamente</summary>

Se o software não foi executado por um longo período e/ou a atualização automática está desabilitada, a versão instalada pode ter perdido suporte e está impossibilitada de receber atualizações. Prossiga com a desinstalação manual e a instalação da versão de software mais recente.

</details>

<details>
<summary>Notificação de incompatibilidade após atualizar</summary>

Verifique os requisitos de sistema na página de download e tente novamente após resolver a incompatibilidade.

</details>

<details>
<summary>Erro de integridade comprometida</summary>

O erro de integridade pode ocorrer em diferentes contextos e resulta nos seguintes efeitos:

- **Instalação ou atualização de software:** pacotes inválidos não serão aplicados.
- **Alteração ilegal no algoritmo:** a integridade de software é restaurada automaticamente.
- **Alterações indevidas no arquivo de backup:** você será notificado e poderá realizar o backup novamente.

</details>

## Backup

<details>
<summary>O que é suporte a multidispositivos e multiusuários?</summary>

Permite adicionar backups de vários dispositivos e usuários na mesma estrutura de backup.

</details>

<details>
<summary>Outro usuário pode fazer backup dos meus dados?</summary>

Não. Workflow opera em nível de usuário, impedindo que outros acessem seus dados locais. No entanto, observe que o backup de dados não é criptografado. É importante garantir que os drives de backup e réplica sejam armazenados de forma segura para proteger seus dados contra acesso não autorizado.

</details>

## Conversão

<details>
<summary>Formato 7z</summary>

7z é um formato moderno e eficiente que utiliza algoritmos avançados, como o LZMA e o LZMA2, para oferecer uma compressão de alta performance e reduzir significativamente o tamanho dos arquivos. Com filtros avançados e compressão sólida – que agrupa arquivos semelhantes para uma compactação mais otimizada – além do suporte à tecnologia multi-threading, o 7z acelera todo o processo, mesmo com arquivos de grande volume. Por ser um formato aberto e gratuito, ele reúne performance e flexibilidade em uma única solução. [Saiba mais][7Zip].

</details>

<details>
<summary>Formato WebP</summary>

WebP é um formato moderno e versátil que oferece compressão lossless, resultando em arquivos menores sem perda de qualidade. Suporta transparência e animações, substituindo de forma eficiente formatos tradicionais como BMP, TIFF, PNG e JPEG. Por ser um formato aberto e gratuito, não há custos com licenciamento ou royalties. Além disso, seu amplo suporte em sistemas operacionais, navegadores e ferramentas de edição o torna uma escolha inteligente em comparação com formatos mais recentes. [Saiba mais][WebP].

</details>

<details>
<summary>Formato FLAC</summary>

FLAC (Free Lossless Audio Codec) é um formato de compressão de áudio sem perda de qualidade, ideal para arquivamento e backups de arquivos de áudio. Ao contrário de formatos com perdas como MP3 ou AAC, o FLAC preserva todos os dados originais, garantindo fidelidade absoluta na reprodução. Sua compactação reduz significativamente o tamanho dos arquivos, sem comprometer a integridade do conteúdo. Por ser um formato aberto, gratuito e amplamente compatível com aplicativos e sistemas operacionais, o FLAC é a escolha perfeita para quem busca qualidade e eficiência no armazenamento de áudio. [Saiba mais][FLAC].

</details>

## Manutenção

<details>
<summary>Verificar Imagem do Sistema</summary>

- Verificar: Aciona o DISM (Deployment Imaging Service and Management Tool) para analisar a integridade da imagem do sistema, buscando possíveis corrupções.

- Reparar: Aciona o DISM para reparar automaticamente a integridade da imagem do sistema utilizando arquivos de reparo disponíveis localmente ou baixando-os dos servidores da Microsoft.

> A disponibilidade de recursos e funcionalidades pode variar conforme a plataforma.

</details>

<details>
<summary>Verificar Instalação do Sistema</summary>

- Verificar: Aciona o SFC (System File Checker) para analisar e reparar arquivos de sistema corrompidos ou ausentes a partir de uma cópia em cache disponível em uma área protegida do sistema.

- Consolidar: Aciona o DISM para limpar e otimizar a imagem do sistema, removendo componentes obsoletos e versões antigas, liberando espaço de armazenamento e melhorando a eficiência geral do sistema.

> A disponibilidade de recursos e funcionalidades pode variar conforme a plataforma.

</details>

## Configuração

<details>
<summary>Exportar hashes de empacotamento</summary>

Habilite o Registro de Eventos para exportar hashes de empacotamento.

</details>

<details>
<summary>Exportar as configurações de software</summary>

- Windows
    - Siga para `Configurações` `>` `Gerenciar` `>` `Exportar`
    - Utilize `WIN+R` e acesse `%UserProfile%\Downloads`
    - Faça backup de `WorkflowSettingsBackup.json`
- Linux
    - Siga para `Configurações` `>` `Gerenciar` `>` `Exportar`
    - Utilize `ALT+F2` e acesse `~/Downloads`
    - Faça backup de `WorkflowSettingsBackup.json`

</details>

<details>
<summary>Transferir configurações para um novo dispositivo</summary>

- Windows
    - No dispositivo antigo:
        - Siga para `Configurações` `>` `Gerenciar` `>` `Exportar`
        - Utilize `WIN+R` e acesse `%UserProfile%\Downloads`
        - Copie o arquivo `WorkflowSettingsBackup.json`
    - No dispositivo novo:
        - Instale o software
        - Utilize `WIN+R` e acesse `%UserProfile%\Downloads`
        - Cole o arquivo `WorkflowSettingsBackup.json`
        - Siga para `Configurações` `>` `Gerenciar` `>` `Importar`
- Linux
    - No dispositivo antigo:
        - Siga para `Configurações` `>` `Gerenciar` `>` `Exportar`
        - Utilize `ALT+F2` e acesse `~/Downloads`
        - Copie o arquivo `WorkflowSettingsBackup.json`
    - No dispositivo novo:
        - Instale o software
        - Utilize `ALT+F2` e acesse `~/Downloads`
        - Cole o arquivo `WorkflowSettingsBackup.json`
        - Siga para `Configurações` `>` `Gerenciar` `>` `Importar`

> Informações de identificação e segurança não podem ser transferidas.

</details>

<details>
<summary>Registro de eventos</summary>

O Registro de Eventos coleta e armazena localmente informações sobre o ambiente, usuário e a execução do software. Esses dados são automaticamente excluídos conforme a Política de Retenção. O usuário pode desativar o Registro de Eventos ou ajustar o período de retenção nas configurações.

Os dados do Registro de Eventos permitem identificar padrões de uso, ajudam a monitorar o desempenho, diagnosticar problemas e manter a cronologia das atividades de software, facilitando a análise retroativa e a recuperação de informações.

Nenhum dado é enviado para a internet.

</details>

<details>
<summary>Modo de Reversão</summary>

O Modo de Reversão protege suas configurações ao executar versões anteriores de software. Todas as alterações são descartadas ao encerrar. O Modo de Reversão é ativado automaticamente e não é possível desativá-lo manualmente.

</details>

## Navegação

Uma visão do mapa de menus da versão mais recente de software.

<details>
<summary>Windows</summary>

```
Home
├─ Backup
│   ├─ Iniciar
│   ├─ Replicar
│   └─ Restaurar
├─ Conversão
│   └─ Pacotes
├─ Diagnóstico
│   ├─ Relatório da Bateria
│   ├─ Verificar Saúde do Drive
│   └─ Verificar Sistema de Arquivos
├─ Manutenção
│   ├─ Gerenciar Aplicativos
│   │   ├─ Listar
│   │   ├─ Atualizar
│   │   ├─ Importar
│   │   └─ Exportar
│   ├─ Desfragmentar
│   │   ├─ Analisar
│   │   ├─ Otimizar
│   │   └─ Trim
│   ├─ Gerenciar Administrador
│   │   ├─ Ativar
│   │   └─ Desativar
│   ├─ Verificar Imagem do Sistema
│   │   ├─ Verificar
│   │   └─ Reparar
│   └─ Verificar Instalação do Sistema
│       ├─ Verificar
│       └─ Consolidar
├─ Configurações
│   ├─ Backup
│   │   ├─ Parâmetros
│   │   │   ├─ Diretório de Backup
│   │   │   ├─ Diretório de Réplica
│   │   │   ├─ Diretório de Restauração
│   │   │   ├─ Período de Retenção
│   │   │   ├─ Nível de Compressão
│   │   │   └─ Replicação Automática
│   │   └─ Conteúdo
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       └─ Disponível
│   ├─ Conversão
│   │   ├─ Diretório de Conversão
│   │   ├─ Incluir Formatos Adicionais
│   │   └─ Preservar Originais
│   ├─ Interface
│   │   ├─ Cor Primária
│   │   └─ Cor Secundária
│   ├─ Notificações
│   │   ├─ Software
│   │   ├─ Backup
│   │   ├─ Conversão
│   │   ├─ Diagnóstico
│   │   └─ Manutenção
│   ├─ Registro de Eventos
│   │   ├─ Estado
│   │   ├─ Período de Retenção
│   │   └─ Exibir
│   ├─ Extensões
│   │   ├─ 7-Zip
│   │   │   ├─ Instalar
│   │   │   ├─ Atualizar
│   │   │   └─ Desinstalar
│   │   ├─ WebP
│   │   │   ├─ Instalar
│   │   │   ├─ Atualizar
│   │   │   └─ Desinstalar
│   │   ├─ FLAC
│   │   │   ├─ Instalar
│   │   │   ├─ Atualizar
│   │   │   └─ Desinstalar
│   │   └─ FFmpeg
│   │       ├─ Instalar
│   │       ├─ Atualizar
│   │       └─ Desinstalar
│   ├─ Empacotar
│   ├─ Gerenciar
│   │   ├─ Importar
│   │   ├─ Exportar
│   │   └─ Redefinir
│   ├─ Atualizar
│   │   ├─ Estado
│   │   └─ Fonte
│   └─ Desinstalar
├─ Sobre
└─ Encerrar
```

</details>

<details>
<summary>Linux</summary>

```
Home
├─ Backup
│   ├─ Iniciar
│   ├─ Replicar
│   └─ Restaurar
├─ Conversão
│   ├─ Pacotes
│   ├─ Imagens
│   └─ Áudios
├─ Diagnóstico
│   └─ Relatório da Bateria
├─ Manutenção
│   ├─ Gerenciar Aplicativos
│   │   ├─ Listar
│   │   ├─ Atualizar
│   │   └─ Exportar
│   └─ Desfragmentar
│       ├─ Analisar
│       ├─ Otimizar
│       └─ Trim
├─ Configurações
│   ├─ Backup
│   │   ├─ Parâmetros
│   │   │   ├─ Diretório de Backup
│   │   │   ├─ Diretório de Réplica
│   │   │   ├─ Diretório de Restauração
│   │   │   ├─ Período de Retenção
│   │   │   ├─ Nível de Compressão
│   │   │   └─ Replicação Automática
│   │   └─ Conteúdo
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       ├─ Disponível
│   │       └─ Disponível
│   ├─ Conversão
│   │   ├─ Diretório de Conversão
│   │   ├─ Incluir Formatos Adicionais
│   │   └─ Preservar Originais
│   ├─ Interface
│   │   ├─ Cor Primária
│   │   └─ Cor Secundária
│   ├─ Notificações
│   │   ├─ Software
│   │   ├─ Backup
│   │   ├─ Conversão
│   │   ├─ Diagnóstico
│   │   └─ Manutenção
│   ├─ Registro de Eventos
│   │   ├─ Estado
│   │   ├─ Período de Retenção
│   │   └─ Exibir
│   ├─ Extensões
│   │   ├─ 7-Zip
│   │   │   ├─ Instalar
│   │   │   ├─ Atualizar
│   │   │   └─ Desinstalar
│   │   ├─ WebP
│   │   │   ├─ Instalar
│   │   │   ├─ Atualizar
│   │   │   └─ Desinstalar
│   │   ├─ FLAC
│   │   │   ├─ Instalar
│   │   │   ├─ Atualizar
│   │   │   └─ Desinstalar
│   │   └─ FFmpeg
│   │       ├─ Instalar
│   │       ├─ Atualizar
│   │       └─ Desinstalar
│   ├─ Empacotar
│   ├─ Gerenciar
│   │   ├─ Importar
│   │   ├─ Exportar
│   │   └─ Redefinir
│   ├─ Atualizar
│   │   ├─ Estado
│   │   └─ Fonte
│   └─ Desinstalar
├─ Sobre
└─ Encerrar
```

</details>

## Estrutura

A estrutura de diretórios de software e backup é projetada para proporcionar a separação lógica dos dados, simplificando a manutenção e escalabilidade. Novos componentes, dispositivos e usuários podem ser facilmente integrados sem perturbar a estrutura existente.

<details>
<summary>Windows</summary>

### Software

```
[Usuário] ─┐
           └─ AppData ─┐
                       └─ Local ─┐
                                 └─ DC ─┐                                 | Diretório raiz
                                        └─ Workflow ─┐                    | Diretório de instalação
                                                     ├─ Software          | Diretório de software
                                                     ├─ Extensions        | Diretório de extensões
                                                     ├─ Events            | Diretório de registro de eventos
                                                     └─ Cache             | Diretório de armazenamento temporário
```

### Backup

```
[Drive] ─┐
         └─ Workflow ─┐                                                   | Diretório raiz
                      └─ [Dispositivo] ─┐                                 | Diretório de controle
                                        └─ [Usuário] ─┐                   | Diretório de controle
                                                      └─ {+}              | Dados
```

</details>

<details>
<summary>Linux</summary>

### Software

```
[Usuário] ─┐
           └─ .DC ─┐                                                      | Diretório raiz
                   └─ Workflow ─┐                                         | Diretório de instalação
                                ├─ Software                               | Diretório de software
                                ├─ Extensions                             | Diretório de extensões
                                ├─ Events                                 | Diretório de registro de eventos
                                └─ Cache                                  | Diretório de armazenamento temporário
```

### Backup

```
[Drive] ─┐
         └─ Workflow ─┐                                                   | Diretório raiz
                      └─ [Dispositivo] ─┐                                 | Diretório de controle
                                        └─ [Usuário] ─┐                   | Diretório de controle
                                                      └─ {+}              | Dados
```

</details>

## Código-fonte

Prepare-se para uma jornada emocionante pelo universo do software livre.

<details>
<summary>Fundamentos da licença GPL</summary>

- **Liberdade 0:** Execute o software como quiser, para qualquer finalidade.
- **Liberdade 1:** Explore e ajuste o software conforme suas necessidades.
- **Liberdade 2:** Compartilhe o software para ajudar outras pessoas.
- **Liberdade 3:** Melhore o software e compartilhe suas inovações com a comunidade.

> Verifique [SPDX.org][SPDX.org] para mais informações.

</details>

<details>
<summary>Acesso ao código-fonte</summary>

- Baixe a versão mais recente de software do repositório.
- Extraia o conteúdo do pacote com um software compatível.
- Abra o arquivo de software `ps1` em um IDE.
- Aproveite a experiência!

</details>

## Softwares de terceiros

### Requisitos

<details>
<summary>PowerShell: Como instalar</summary>

- Windows
    - Abra o terminal
    - Instale o pacote `winget install --id Microsoft.PowerShell --source winget`

- Linux
    - Abra o terminal
    - Instale o pacote `snap install powershell`

> Pode requerer elevação de privilégios

</details>

<details>
<summary>Windows: Acesso a Pastas Controladas</summary>

Alguns recursos precisam de acesso a pastas de usuário ou aplicativos. Adicione o PowerShell e o 7-Zip ao Acesso a Pastas Controladas nas configurações de segurança do Windows.

</details>

### Extensões

<details>
<summary>Como instalar</summary>

Siga para `Configurações` `>` `Extensões`

> Pode requerer elevação de privilégios

> As extensões foram movidas para a estrutura de diretórios de software em ambiente **Linux** na versão **25.05.0**. Workflow não utilizará os binários das extensões disponíveis no `$PATH` do sistema, com exceção das extensões FFmpeg e FLAC. Essa mudança permite um controle preciso de instalação, atualização e versionamento de extensões a partir do repositório ou site oficial, sem interferir nos binários instalados via APT e reduzindo a necessidade de elevação de privilégios para a instalação de softwares adicionais.

</details>

<details>
<summary>Como atualizar</summary>

Siga para `Configurações` `>` `Extensões`

> Pode requerer elevação de privilégios

</details>

<details>
<summary>Como desinstalar</summary>

Siga para `Configurações` `>` `Extensões`

> Pode requerer elevação de privilégios

</details>

### Fontes

<details>
<summary>Como instalar</summary>

Para um design agradável, moderno e sofisticado no terminal, prefira a fonte [JetBrains Mono][JetBrains Mono]. Adicionalmente você pode utilizar [Cascadia Mono][Cascadia Mono], [Ubuntu Mono][Ubuntu Mono] ou [Noto Sans Mono][Noto Sans Mono].

- Windows
    - Método 1
        - Clique com o botão direito do mouse no arquivo de fonte
        - Clique em Instalar
    - Método 2 (Windows 10 ou superior)
        - Copie a fonte para o diretório do sistema `C:\Windows\Fonts`
- Linux
    - Método 1
        - Clique com o botão direito do mouse no arquivo de fonte
        - Clique em Instalar
    - Método 2
        - Copie a fonte para o diretório do sistema `sudo cp * /usr/local/share/fonts`
        - Atualize o cache de fontes do sistema `sudo fc-cache --force --verbose`

</details>

[Evolução]: /Evolution.md
[Política de Suporte]: /Policies.md
[7zip]: https://www.7-zip.org/7z.html
[WebP]: https://developers.google.com/speed/webp
[FLAC]: https://xiph.org/flac/documentation.html
[SPDX.org]: https://spdx.org/licenses/GPL-3.0-or-later.html
[JetBrains Mono]: https://fonts.google.com/specimen/JetBrains+Mono
[Cascadia Mono]: https://fonts.google.com/specimen/Cascadia+Mono
[Ubuntu Mono]: https://fonts.google.com/specimen/Ubuntu+Mono
[Noto Sans Mono]: https://fonts.google.com/noto/specimen/Noto+Sans+Mono