última atualização: 18/06/2026 

Produzido por: 

Vinicius Borba 

## **Active Directory Security Architecture Guide** 

- Designing a Blue Team Oriented Enterprise Environment 

última atualização: 18/06/2026 

Produzido por: 

Vinicius Borba 

1. Introdução ....................................................................................................... 1 2. Estrutura do Domínio ........................................................................................ 1 3. Estrutura de Usuários ....................................................................................... 1 4. Estrutura de Estações de trabalho ..................................................................... 1 5. Estrutura de Estações de trabalho ..................................................................... 1 

última atualização: 18/06/2026 

Produzido por: 

Vinicius Borba 

## **1. Introdução** 

Este projeto tem como objetivo demonstrar uma implementação de Active Directory focada em boas práticas de administração, segurança e governança. 

A estrutura foi desenvolvida para estudos de Blue Team, Hardening, Controle de Acesso, Gestão de Identidades e Segurança Defensiva. 

Os principais objetivos são: 

- Organização lógica dos objetos do domínio. 

- Aplicação granular de Group Policies (GPOs). 

- Separação de privilégios administrativos. 

- Facilidade de auditoria. 

- Implementação de Hardening baseado em CIS Benchmarks. 

- Preparação para projetos futuros de SIEM, DLP e Zero Trust. 

## **2. Estrutura do Domínio** 

Domínio utilizado: 

**==> picture [335 x 46] intentionally omitted <==**

**----- Start of picture text -----**<br>
vsecurity.net<br>**----- End of picture text -----**<br>


A estrutura foi dividida em quatro grandes áreas: 

**Users_VSecurity Workstations_VSecurity Servers_VSecurity Groups_VSecurity** 

última atualização: 18/06/2026 

Produzido por: 

Vinicius Borba 

## **3. Estrutura de Usuários** 

## **Users_VSecurity** 

## **Users_VSecurity** 

Esta OU centraliza todos os objetos relacionados a usuários. 

## **Admins** 

## **Users_VSecurity > Admins** 

Contém contas administrativas utilizadas exclusivamente para administração do ambiente. Como por exemplo: 

Admin.borba 

Admin.sysadmin 

Admin.contoso 

Justificativa: Separar contas administrativas das contas comuns reduz o risco de comprometimento de privilégios elevados. 

## **Privileged Users** 

## **Users_VSecurity > Privileged Users** 

Destinada a usuários com permissões elevadas específicas. Como por exemplo: 

Backup Operators 

Account Operators 

DNS Administrators 

## **Service Accounts** 

## **Users_VSecurity > Service Accounts** 

Armazena contas utilizadas por serviços e aplicações. Como por exemplo: 

última atualização: 18/06/2026 

Produzido por: 

Vinicius Borba 

Svc_glpi Svc_wazuh Svc_backup 

Boas Práticas para estes usuários em específico são: 

Senhas complexas; Logon interativo bloqueado; Rotação periódica; Monitoramento contínuo; 

## **Standard Users** 

## **Users_VSecurity > Standard Users** 

Contém usuários corporativos separados por departamento. 

**==> picture [199 x 242] intentionally omitted <==**

**----- Start of picture text -----**<br>
01 - Executive Board<br>02 - Finance Department<br>03 - Controllership<br>04 - Information Technology<br>05 - Human Resources<br>06 - Sales Department<br>07 - Marketing Department<br>**----- End of picture text -----**<br>


Tratando o ambiente desta forma, teremos os seguintes benefícios: 

- Aplicação de GPO específica por setor. 

- Controle de acesso granular. 

- Delegação administrativa. 

última atualização: 18/06/2026 

Produzido por: 

Vinicius Borba 

última atualização: 18/06/2026 

Produzido por: 

Vinicius Borba 

## **4. Estrutura de Estações de trabalho** 

## **VSecurity.net > Workstations_VSecurity** 

Responsável pela organização dos computadores corporativos. 

Estrutura: 

- Financeiro: Bloqueio de USB, Restrições de software. 

- TI: Ferramentas administrativas liberadas. 

- Diretoria: Configurações diferenciadas de segurança. 

## **5. Estrutura de Estações de Servidores** 

**==> picture [251 x 41] intentionally omitted <==**

**----- Start of picture text -----**<br>
VSecurity.net > Servers_VSecurity<br>**----- End of picture text -----**<br>


Separação entre ambientes. 

última atualização: 18/06/2026 

Produzido por: 

Vinicius Borba 

**==> picture [250 x 96] intentionally omitted <==**

**----- Start of picture text -----**<br>
Servers_VSecurity<br>├ ── Production<br>└── Staging<br>**----- End of picture text -----**<br>


## **Production** 

Ambiente de produção. 

**==> picture [143 x 201] intentionally omitted <==**

**----- Start of picture text -----**<br>
>Production<br>- Application<br>- Domain Controller<br>- Jump<br>- Linux<br>- Monitoring<br>**----- End of picture text -----**<br>


## **Staging** 

Ambiente de Homologação, tem como objetivo realizar testes antes de ser utilizado em produção 

**==> picture [143 x 201] intentionally omitted <==**

**----- Start of picture text -----**<br>
>Production<br>- Application<br>- Domain Controller<br>- Jump<br>- Linux<br>- Monitoring<br>**----- End of picture text -----**<br>


última atualização: 18/06/2026 

Produzido por: 

Vinicius Borba 

## **6. Estrutura de Grupos** 

## **VSecurity.net > Groups_VSecurity** 

Centralização dos grupos de segurança. Estes grupos tem como objetivo realizar e liberar permissões especificas de acordo com a necessidade. 

**==> picture [203 x 201] intentionally omitted <==**

**----- Start of picture text -----**<br>
- Administrative Groups<br>- Distribution Groups<br>- File Permissions<br>- Role Groups<br>- Security Groups<br>- Service Groups<br>**----- End of picture text -----**<br>


Como por exemplo: GRP-DOMAIN-ADMINS = Tem permissão para gerenciar os domínios do ambiente. 

## **6. Estrutura de Grupos** 

## **Esta arquitetura oferece:** 

- **Segurança:** Menor superfície de ataque, Separação de privilégios, Aplicação granular de GPOs. 

- **Administração** : Facilidade de gerenciamento, e escalabilidade, Padronização 

- **Auditoria:** Melhor rastreabilidade, Facilidade para investigações. 

- **Compliance:** Compatível com CIS Controls, compatível com boas práticas Microsoft. 

