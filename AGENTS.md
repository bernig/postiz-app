# Agent guidance - Postiz

Monorepo Postiz (NESTJS backend/orchestrator + React/Vite frontend, pnpm). Contexte projet détaillé
dans `CLAUDE.md`. Mémoire dans `.remember/`.

## Mémoire entre sessions (Claude Code + Cline, interchangeable)

**Store mémoire unique** : `.remember/` (accumulateur local, non commité, perms 600) : journaux
`today-YYYY-MM-DD.md`, `now.md`, `recent.md`, `archive.md`. Il est utilisé tel quel, que l'on
travaille avec Claude Code ou avec Cline (y compris avec des modèles non-Anthropic) — **pas de
deuxième système de mémoire parallèle**.

**Fichiers d'instructions** : `AGENTS.md` (Cline / modèles non-Anthropic) et `CLAUDE.md`
(Claude Code) décrivent tous deux ce même store `.remember/` et la même règle de promotion.

**Règle (esprit memory-merger)** : on accumule les appris au fil de l'eau dans `.remember/` ;
quand un apprentissage devient mature et réutilisable, on le « promeut » dans ce fichier
d'instructions (dédup, zéro redondance, scannabilité maximale) et on signale la promotion dans
le journal mémoire. Le fichier d'instructions reste la référence « stable » à relire ;
`.remember/` reste l'accumulateur.