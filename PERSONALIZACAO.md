# Personalizações da Cannabcura

Fork de [soucannabis/kunk-soucannabis](https://github.com/soucannabis/kunk-soucannabis) (AGPL-3.0) adaptado para a Associação Cannabcura.

Este arquivo lista tudo que foi alterado em relação ao original. Ao trazer atualizações pelo **Sync fork**, confira estes arquivos primeiro: são os que podem gerar conflito.

## Identidade visual

A maior parte é configurada pelo Admin e fica no banco de dados, não no código:

- **Admin → Dados da associação:** logos, nome, contatos, textos do cadastro.
- **Admin → Kunk → Aparência:** cores (menu `#587141`, fundo escuro `#263020`, destaque `#8cd207`).

### Alterações no código

| Arquivo | O que mudou |
| --- | --- |
| `apps/admin/src/layout/AdminShell.jsx` | Texto abaixo da logo no menu do Admin: "Kunk Admin" → "Administrador" |

## Cadastro: nome e WhatsApp na criação da conta

Antes, a primeira tela do cadastro pedia só e-mail e senha. Quem parava ali ficava sem telefone para contato. Agora a tela pede **nome e WhatsApp**, que já aparecem preenchidos na etapa "Dados do responsável".

| Arquivo | O que mudou |
| --- | --- |
| `apps/registration/src/pages/AuthPages.jsx` | Campos Nome e WhatsApp na tela de cadastro, com validação |
| `packages/auth-session/src/index.jsx` | `registerEmail` repassa nome e telefone |
| `packages/api-client/src/index.js` | `registerEmail` envia nome e telefone à API |
| `kunk-api/src/routes/authAssociate.js` | Rota `/auth/associate/register-email` recebe `associate_name` e `mobile_number` |
| `kunk-api/src/repositories/associateAuthRepository.js` | Grava nome e celular (só dígitos) ao criar a conta. Os campos são opcionais na API |

## Não versionado

- `.env` (já ignorado pelo projeto): nunca enviar senhas ou chaves.
- Scripts de teste `*.local.cjs` e a pasta de logos: ignorados localmente.
