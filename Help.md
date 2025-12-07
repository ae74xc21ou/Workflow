# Ajuda

Um guia para instalação e execução de software. Encontre soluções para problemas comuns, instruções de atualização, configuração e dicas para o uso de funcionalildades.

## Primeiros Passos

### Fontes

<details>
<summary>O que são Fontes</summary>

Fontes são canais de distribuição de software que podem ser remotas, locais ou personalizadas, usadas para instalação e atualização.

Permitir a seleção entre fontes é uma estratégia flexível que aumenta a disponibilidade do software, dando aos usuários a opção entre atualização automática e controle local. O recurso atende a cenários de desenvolvimento, produção e emergência e possibilita estratégias híbridas, combinando automação com segurança e redundância para rollback.

</details>

<details>
<summary>Escolher uma Fonte</summary>

Todas as abordagens oferecem vantagens, e a escolha depende da prioridade entre controle, velocidade e disponibilidade.

- Fonte remota
    - Ideal para usuários que priorizam agilidade e integração contínua.
    - Distribuição global com menor latência via infraestrutura de CDN;
    - Acesso imediato a atualizações assim que publicadas no repositório oficial.
- Fonte local
    - Ideal para ambientes pessoais, isolados ou com restrições de rede;
    - Operação totalmente offline, sem dependência de conexão com a internet;
    - Controle total sobre hospedagem, atualizações de software e rollback.
- Fonte personalizada
    - Ideal para organizações que buscam independência completa de plataformas públicas;
    - Controle total sobre o ciclo de desenvolvimento, hospedagem e distribuição conforme políticas internas.

</details>

<details>
<summary>Locais das Fontes</summary>

- Fonte remota: repositório oficial do projeto no **GitHub**.
- Fonte local: diretório **Downloads** do usuário local.
- Fonte personalizada: Configurável a partir da rede local.

</details>

<details>
<summary>Provisionar uma Fonte</summary>

Provisionar uma fonte significa preparar os arquivos de instalação e atualização para que possam ser usados a partir de uma fonte local ou personalizada.

- **Obter:** Baixe os **pacotes** de software e o arquivo **Metadata.json** a partir do repositório oficial ou utilize uma versão interna.
- **Armazenar:** Copie os arquivos para o diretório desejado.
- **Validar:** Verifique o hash dos pacotes de software para garantir que estejam íntegros.
- **Configurar:** No software, ajuste a configuração para usar a fonte adequada.
- **Testar:** Execute uma instalação ou atualização de teste para validar a fonte configurada.

> Mantenha o nome dos arquivos conforme disponibilizado no repositório oficial, para evitar falhas de reconhecimento.

</details>

### Instalação

<details>
<summary>Como Instalar</summary>

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

> Ao executar pela primeira vez, você precisará escolher uma fonte de software. Prefira a fonte **Remota**. Caso contrário, verifique como provisionar uma fonte.
    
</details>

<details>
<summary>Como Executar</summary>

Após a instalação, você pode usar o atalho criado no diretório do usuário local para executar o software.

- Windows
    - Abra o PowerShell;
    - Navegue até a pasta inicial `Set-Location $Home`;
    - Execute `.\Workflow.ps1`.
- Linux
    - Abra o PowerShell `pwsh`;
    - Navegue até a pasta inicial `Set-Location $Home`;
    - Execute `./Workflow.ps1`.

</details>

<details>
<summary>Como Desinstalar</summary>

Siga para `Configurações` `>` `Desinstalar`.

</details>

<details>
<summary>O Software não é Instalado Automaticamente</summary>

Você está executando uma versão de software sem suporte ou selecionou uma fonte de software não provisionada. Utilize a versão mais recente e verifique a fonte configurada antes de prosseguir. Verifique [Política de Suporte][Política de Suporte] para mais informações.

</details>

<details>
<summary>Atalho Ausente no Diretório do Usuário</summary>

Caso o atalho `Workflow.ps1` esteja ausente no diretório `$Home`, verifique o tópico **Acesso a Pastas Controladas** na seção **Software de Terceiros**. Em seguida execute Workflow manualmente a partir do diretório de instalação de software `%UserProfile%\AppData\Local\DC\Workflow\Software` para que o atalho seja recriado automaticamente.

</details>

### Atualização

<details>
<summary>Como Atualizar</summary>

Prossiga conforme a fonte configurada:

- Fonte remota
    - Mantenha-se online;
    - Habilite a atualização automática;
    - Execute o software regularmente.
- Fonte local
    - Mantenha a fonte local provisionada e atualizada adequadamente;
    - Habilite a atualização automática;
    - Execute o software regularmente.
- Fonte personalizada
    - Mantenha a fonte personalizada provisionada e atualizada adequadamente;
    - Habilite a atualização automática;
    - Execute o software regularmente.

</details>

<details>
<summary>O Software não Recebe Atualizações Automaticamente</summary>

A fonte de software está configurada incorretamente ou não provisionada; a atualização automática está desabilitada; o software não é executado há muito tempo. Neste cenário a versão instalada pode ter perdido suporte e está impossibilitada de receber atualizações. Prossiga com a desinstalação manual e a instalação da versão de software mais recente. Verifique [Evolução][Evolução] e [Política de Suporte][Política de Suporte] para mais informações.

</details>

## Fluxos

### Backup

<details>
<summary>Multidispositivos e Multiusuários</summary>

O suporte a multidispositivos e multiusuários de Workflow permite armazenar backups de vários dispositivos e usuários na mesma estrutura de backup.

Workflow opera em nível de usuário, impedindo que outros acessem seus dados locais. No entanto, o backup de dados não é criptografado. É importante garantir que os diretórios de backup e réplica sejam armazenados de forma segura para proteger seus dados contra acesso não autorizado.

```
[Configurável] ┐                                                           | Diretório de backup/replica
               └ Workflow ┐                                                | Diretório de armazenamento
                          └ [Dispositivo] ┐                                | Diretório de controle
                                          └ [Usuário] ┐                    | Diretório de controle
                                                      └ {+}                | Dados
```

</details>

<details>
<summary>Período de Retenção</summary>

O Período de Retenção define por quanto tempo os arquivos de backup e réplica serão mantidos. Após esse período, Workflow remove automaticamente os itens mais antigos, preservando apenas os arquivos dentro da janela configurada.

Esse recurso mantém o diretório de armazenamento organizado, evita acúmulo desnecessário de dados e ajuda a controlar o uso de espaço em disco. O usuário pode ajustar o período conforme sua estratégia de backup, capacidade de armazenamento e necessidade de histórico.

</details>

<details>
<summary>Níveis de Compressão</summary>

Os níveis de compressão definem o equilíbrio entre desempenho e eficiência no tamanho do arquivo final. Workflow utiliza o algoritmo **LZMA2** e ajusta automaticamente o uso de memória e o nível de análise conforme a configuração selecionada.

- **Nível Mínimo:** Prioriza velocidade e baixo consumo de memória. O processamento é rápido e o impacto no sistema é mínimo, mas o tamanho final do backup é maior.
- **Níveis Baixo e Médio:** Oferecem um equilíbrio adequado entre tempo de processamento, uso de recursos e redução do tamanho do arquivo. Recomendados para a maioria dos cenários.
- **Níveis Alto e Máximo:** Utilizam mais memória e exigem maior tempo de processamento para obter a melhor taxa de compactação possível. Adequados para dispositivos com maior capacidade ou backups de grande volume.

Durante a compressão, Workflow ajusta automaticamente:

- Intensidade da compressão.
- Consumo de memória proporcional ao nível selecionado.
- Pofundidade da análise de dados.

Essa combinação garante resultados consistentes, permitindo ao usuário escolher entre velocidade, economia de recursos ou máxima compactação conforme a necessidade.

</details>

<details>
<summary>Replicação Automática</summary>

A Replicação Automática copia os arquivos de backups para o diretório de réplica configurado, garantindo uma segunda cópia dos dados sem intervenção do usuário. Quando habilitada, a replicação ocorre imediatamente após o término do processo de backup.

Esse recurso reduz riscos de perda de dados ao manter uma cópia adicional em um local independente do diretório de backup. A execução é totalmente automatizada e não exige agendamento, tornando a proteção dos dados contínua e previsível.

</details>

### Conversão

<details>
<summary>Pacotes</summary>

- **Formatos de Entrada:** `.tar.gz`, `.tar.bz2`, `.tar.xz`, `.tar.zst`, `.tar`, `.zip`, `.rar`

- **Formato de Saída:** `7z` é um formato moderno e eficiente que utiliza algoritmos avançados, como LZMA2, para oferecer uma compressão de alta performance e reduzir significativamente o tamanho dos arquivos. Com filtros avançados e compressão sólida, que agrupam arquivos semelhantes para uma compactação mais otimizada, além do suporte à tecnologia multi-threading, o 7z acelera todo o processo, mesmo com arquivos de grande volume. Por ser um formato aberto e gratuito, ele reúne performance e flexibilidade em uma única solução. [Saiba mais][7Zip].

</details>

<details>
<summary>Imagens</summary>

- **Formatos de Entrada:** `.jpg`, `.jpeg`, `.tif`, `.tiff`, `.png`, `.bmp`

- **Formato de Saída:** `WebP` é um formato moderno e versátil que oferece compressão lossless, resultando em arquivos menores sem perda de qualidade. Suporta transparência e animações, substituindo de forma eficiente formatos tradicionais como BMP, TIFF, PNG e JPEG. Por ser um formato aberto e gratuito, não há custos com licenciamento ou royalties. Além disso, seu amplo suporte em sistemas operacionais, navegadores e ferramentas de edição o torna uma escolha inteligente em comparação com formatos mais recentes. [Saiba mais][WebP].

</details>

<details>
<summary>Áudios</summary>

- **Formatos de Entrada:** `.raw`, `.wav`, `.aif`, `.aiff`, `.mp3`, `.aac`, `.wma`, `.m4a`

- **Formato de Saída:** `FLAC` (Free Lossless Audio Codec) é um formato de compressão de áudio sem perda de qualidade, ideal para arquivamento e backups de arquivos de áudio. Ao contrário de formatos com perdas como MP3 ou AAC, o FLAC preserva todos os dados originais, garantindo fidelidade absoluta na reprodução. Sua compactação reduz significativamente o tamanho dos arquivos, sem comprometer a integridade do conteúdo. Por ser um formato aberto, gratuito e amplamente compatível com aplicativos e sistemas operacionais, o FLAC é a escolha perfeita para quem busca qualidade e eficiência no armazenamento de áudio. [Saiba mais][FLAC].

</details>

<details>
<summary>Vídeos</summary>

- **Formatos de Entrada:** `.mov`, `.avi`, `.mpg`, `.wmv`, `.mp4`

- **Formato de Saída:** `MKV` (Matroska Video) é um formato multimídia aberto e flexível que suporta múltiplas faixas de vídeo, áudio, legendas e metadados em um único arquivo. Essa versatilidade o torna ideal para arquivamento e distribuição de mídia em alta qualidade, mantendo compatibilidade com uma ampla gama de players e ferramentas de edição. Utilizado em conjunto com os codecs **VP9** (vídeo) e **FLAC** (áudio), garante alta eficiência de compressão sem perdas visuais e sonoras. O VP9 proporciona excelente relação entre qualidade e tamanho de arquivo em vídeos de alta definição, enquanto o FLAC assegura fidelidade absoluta na reprodução do áudio. Essa combinação oferece uma solução moderna, gratuita e livre de royalties, equilibrando desempenho, qualidade e acessibilidade. [Saiba mais][MKV].

</details>

<details>
<summary>Limite de Processamento</summary>

O Limite de Processamento define quantos arquivos serão convertidos em uma única execução. Quando o número de itens disponíveis excede o limite configurado, apenas os primeiros arquivos são processados e a conversão é encerrada ao atingir o limite. Os demais itens permanecem disponíveis para conversão, permitindo que o usuário inicie uma nova execução posteriormente.

Esse recurso evita operações excessivamente longas em cenários com grande volume de arquivos e oferece maior previsibilidade no tempo de execução, permitindo ao usuário ajustar o limite conforme sua rotina e capacidade do dispositivo.

</details>

<details>
<summary>Preservar Originais</summary>

Quando habilitada, a opção Preservar Originais mantém os arquivos de entrada no diretório de conversão após a conclusão do processo. Workflow não remove o conteúdo original automaticamente, permitindo que o usuário decida quando e como descartá-lo.

Essa opção é útil se você prefere revisar o resultado da conversão antes de excluir os arquivos originais ou para cenários em que é necessário manter uma cópia intacta dos dados de entrada.

</details>

### Manutenção

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

## Configurações

### Monitoramento

<details>
<summary>Eventos</summary>

O Registro de Eventos coleta e armazena localmente informações sobre o ambiente, usuário e a execução do software. Esses dados são automaticamente excluídos conforme a Política de Retenção. O usuário pode desativar o Registro de Eventos ou ajustar o período de retenção nas configurações.

Os dados do Registro de Eventos permitem identificar padrões de uso, ajudam a monitorar o desempenho, diagnosticar problemas e manter a cronologia das atividades de software, facilitando a análise retroativa e a recuperação de informações.

Nenhum dado é enviado para a internet.

</details>

<details>
<summary>Bateria</summary>

A Verificação de Bateria impede a execução de funcionalidades que demandam maior poder de processamento quando o nível atual estiver abaixo do valor configurado. Quando essa condição é identificada, a execução é interrompida e o usuário pode autorizar manualmente a continuidade, garantindo maior segurança em dispositivos móveis ou com baixo nível de bateria.

Esse controle evita interrupções inesperadas e protege a integridade das operações, especialmente em fluxos que exigem tempo prolongado de execução ou uso intensivo de recursos. O nível pode ser configurado conforme a necessidade do usuário e o perfil de uso do dispositivo.

</details>

### Segurança

<details>
<summary>Integridade</summary>

A Verificação de Integridade monitora a integridade de software, atualizações e backups com o uso de funções de hash criptográficas, garantindo operações de software confiáveis e seguras.

</details>

<details>
<summary>Sentinela</summary>

A Verificação de Sentinela monitora arquivos críticos com o uso de identificadores únicos globais e funções de hash criptográficas, detectando e isolando inconsistências ou corrupções.

</details>

<details>
<summary>Autorização</summary>

A Solicitação de Autorização exige confirmação explícita do usuário ao executar operações críticas, como uso intensivo de recursos, ou alteração de estados de software, evitando que mudanças relevantes ocorram sem supervisão direta.

</details>

### Manutenção

<details>
<summary>Exportar as Configurações de Software</summary>

- Windows
    - Siga para `Configurações` `>` `Manutenção` `>` `Exportar`
    - Utilize `WIN+R` e acesse `%UserProfile%\Downloads`
    - Faça backup de `WorkflowSettingsBackup.json`
- Linux
    - Siga para `Configurações` `>` `Manutenção` `>` `Exportar`
    - Utilize `ALT+F2` e acesse `~/Downloads`
    - Faça backup de `WorkflowSettingsBackup.json`

</details>

<details>
<summary>Transferir as Configurações de Software</summary>

- Windows
    - No dispositivo antigo:
        - Siga as instruções do tópico **Exportar as Configurações de Software**
    - No dispositivo novo:
        - Instale o software
        - Utilize `WIN+R` e acesse `%UserProfile%\Downloads`
        - Cole o arquivo `WorkflowSettingsBackup.json`
        - Siga para `Configurações` `>` `Manutenção` `>` `Importar`
- Linux
    - No dispositivo antigo:
        - Siga as instruções do tópico **Exportar as Configurações de Software**
    - No dispositivo novo:
        - Instale o software
        - Utilize `ALT+F2` e acesse `~/Downloads`
        - Cole o arquivo `WorkflowSettingsBackup.json`
        - Siga para `Configurações` `>` `Manutenção` `>` `Importar`

> Informações de identificação e segurança não podem ser transferidas.

</details>

## Modos

<details>
<summary>Reversão</summary>

O Modo de Reversão protege suas configurações ao executar versões anteriores de software. Todas as alterações são descartadas ao encerrar. O Modo de Reversão é ativado automaticamente e não é possível desativá-lo manualmente.

</details>

## Softwares de Terceiros

### Requisitos

<details>
<summary>PowerShell: Como Instalar</summary>

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
<summary>Como Instalar</summary>

Siga para `Configurações` `>` `Extensões`

> Pode requerer elevação de privilégios

> As extensões foram movidas para a estrutura de diretórios de software em ambiente **Linux** na versão **25.05.0**. Workflow não utilizará os binários das extensões disponíveis no `$PATH` do sistema, com exceção das extensões FFmpeg e FLAC. Essa mudança permite um controle preciso de instalação, atualização e versionamento de extensões a partir do repositório ou site oficial, sem interferir nos binários instalados via APT e reduzindo a necessidade de elevação de privilégios para a instalação de softwares adicionais.

</details>

<details>
<summary>Como Atualizar</summary>

Siga para `Configurações` `>` `Extensões`

> Pode requerer elevação de privilégios

</details>

<details>
<summary>Como Desinstalar</summary>

Siga para `Configurações` `>` `Extensões`

> Pode requerer elevação de privilégios

</details>

### Fontes

<details>
<summary>Como Instalar</summary>

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
        - Copie a fonte para o diretório do sistema `sudo cp -r * /usr/local/share/fonts`
        - Atualize o cache de fontes do sistema `sudo fc-cache --force --verbose`

</details>

## Código-fonte

Prepare-se para uma jornada emocionante pelo universo do software livre.

<details>
<summary>Fundamentos da Licença GPL</summary>

- **Liberdade 0:** Execute o software como quiser, para qualquer finalidade.
- **Liberdade 1:** Explore e ajuste o software conforme suas necessidades.
- **Liberdade 2:** Compartilhe o software para ajudar outras pessoas.
- **Liberdade 3:** Melhore o software e compartilhe suas inovações com a comunidade.

> Verifique [SPDX.org][SPDX.org] para mais informações.

</details>

<details>
<summary>Acesso ao Código-fonte</summary>

- Baixe a versão mais recente de software do repositório.
- Extraia o conteúdo do pacote com um software compatível.
- Abra o arquivo de software `ps1` em um IDE.
- Aproveite a experiência!

</details>

[Política de Suporte]: /Policies.md
[7zip]: https://www.7-zip.org/7z.html
[WebP]: https://developers.google.com/speed/webp
[FLAC]: https://xiph.org/flac/documentation.html
[MKV]: https://www.matroska.org/what_is_matroska.html
[SPDX.org]: https://spdx.org/licenses/GPL-3.0-or-later.html
[JetBrains Mono]: https://fonts.google.com/specimen/JetBrains+Mono
[Cascadia Mono]: https://fonts.google.com/specimen/Cascadia+Mono
[Ubuntu Mono]: https://fonts.google.com/specimen/Ubuntu+Mono
[Noto Sans Mono]: https://fonts.google.com/noto/specimen/Noto+Sans+Mono