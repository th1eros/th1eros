# Security Policy

## Supported Versions

| Branch | Ambiente | Suportado |
|---|---|---|
| `main` | abitat — produção (rapsodia.th1eros.com) | ✅ |
| `develop` | malebolge — staging (rapsodia.th1eros.dev) | ✅ |
| Releases < v1.0 | — | ❌ |

## Reporting a Vulnerability

**Não abra uma Issue pública.**

Chave pública PGP: https://github.com/th1eros.gpg

### Incluir no relatório

- [ ] Descrição da vulnerabilidade
- [ ] Passos para reproduzir
- [ ] Versão afetada (commit hash ou tag) e ambiente (abitat ou malebolge)
- [ ] Impacto potencial (CVSS estimado)
- [ ] Prova de conceito, se possível
- [ ] Sugestão de correção, se houver

### Tempo de resposta

- **Confirmação:** 48h
- **Análise inicial:** 5 dias úteis
- **Correção:** 15–30 dias, conforme severidade

## Scope

| Componente | Escopo |
|---|---|
| **Blue** (Onmega / Gerent) — API, SIEM, análise | ✅ |
| **Red** (Arcanjus / Push) — worker pentest | ✅ |
| **Silver** (Atemporal / In_telectus) — infra compartilhada, Orleans, IA | ✅ |
| **Violet** (Sanctum / Limbo) — orquestração de labs efêmeros | ✅ |
| Frontend HTMX (servido via Nginx) | ✅ |
| Imagens Docker (chiseled em produção, jammy em staging) | ✅ |
| Nginx / Traefik | ✅ |
| CI/CD (GitHub Actions) | ✅ |
| Oracle Autonomous DB | ❌ (Oracle Corp.) |
| Cloudflare Tunnel | ❌ (Cloudflare Inc.) |

## Out of Scope

- Dependências de terceiros não modificadas
- Força bruta contra infraestrutura do servidor
- Vulnerabilidades que exijam acesso físico
- Issues de SEO ou boas práticas sem impacto de segurança

## Legal Notice

Red contém ferramentas de pentest ativo (Nmap, Metasploit, Hydra). Não inclui módulos de pós-exploração, persistência, movimento lateral ou exfiltração — escopo deliberadamente restrito a scan e detecção. Uso sem autorização escrita do proprietário do alvo é ilegal. Restrito a ambientes autorizados ou laboratórios controlados (Violet).

## Disclosure Policy

- **Day 0:** Relatório recebido
- **Day 2:** Confirmação enviada ao reporter
- **Day 5:** Análise inicial concluída
- **Day 15–30:** Patch desenvolvido e testado
- **Day 30:** CVE solicitado, se aplicável
- **Day 45:** Divulgação pública coordenada

## Recognition

### Hall da Fama

| Reporter | Vulnerabilidade | Data |
|---|---|---|
| — | — | — |

### Recompensas

Sem recompensa financeira. Reporter recebe:
- Crédito no Hall da Fama
- Agradecimento público pós-patch
- Convite para beta de novas versões

## Security Measures

### Implementado

- [x] JWT com validação de scope por serviço (`blue:*`, `silver:*`)
- [x] Resolução de chave JWT fail-closed (rejeita placeholder não resolvido)
- [x] CORS via `CORS_ALLOWED_ORIGINS` (sem hardcoding)
- [x] Rate Limiting em endpoints de auth e API
- [x] 2FA via email
- [x] Segredos via `.env` por serviço, nunca versionado
- [x] Imagens chiseled em produção (sem shell)
- [x] CI/CD via GitHub Actions (build, healthcheck, deploy)
- [x] GPG Signed Commits
- [x] SBOM, OpenSSF Scorecard, checksums SHA256 nas releases
- [x] HTTPS via Cloudflare Tunnel

### Em implementação

- [ ] SAST
- [ ] Dependency scanning no CI/CD (Dependabot)
- [ ] Isolamento de rede por laboratório (Violet)
- [ ] Code review obrigatório

## Compliance

- LGPD / GDPR: proteção de dados pessoais
- ISO 27001: controles de acesso
- NIST CSF
- Metodologia: OWASP Top 10, MITRE ATT&CK (ver `PENTEST.md`)
- Critérios de severidade: ver `JULGO.md`

## Contact

- GitHub: [@th1eros](https://github.com/th1eros) · [@ab1tat](https://github.com/ab1tat)
- PGP: [7F0B34DD19233814](https://github.com/th1eros.gpg)

---
*Atualizado: 29 de junho de 2026 · Template base: OpenSSF*
