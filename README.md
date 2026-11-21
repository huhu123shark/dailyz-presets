# dailyz-presets

**Catalogue public des modèles de routine de [Dailyz](https://github.com/huhu123shark/Dailyz).**

Ce dépôt ne contient volontairement qu'une seule chose : [`presets.json`](./presets.json).
L'application Dailyz le télécharge en lecture seule (au plus une fois par 24 h) pour
proposer des suggestions de tâches sans qu'une nouvelle version de l'application soit
nécessaire.

```text
https://raw.githubusercontent.com/huhu123shark/dailyz-presets/main/presets.json
```

## Pourquoi un dépôt séparé

Le code source de Dailyz est privé (il contiendra à terme des identifiants de
monétisation, des clés de signature et des secrets qui ne doivent jamais être
exposés). Seul ce catalogue est public : il sert de source de vérité unique et
permet de corriger ou d'enrichir les modèles sans publier une mise à jour.

## Format d'une entrée

| Champ | Type | Obligatoire | Description |
| --- | --- | --- | --- |
| `id` | `string` | oui | Identifiant stable et unique (kebab-case). |
| `title` | `string` | oui | Nom affiché dans le formulaire. |
| `keywords` | `string[]` | oui | Mots-clés de recherche, en français et en anglais si possible, sans accent requis. |
| `url` | `string` | oui | Lien en `http(s)` vers la page à ouvrir. |
| `durationMinutes` | `number` | non | Durée conseillée, entre 1 et 240 minutes. |

```json
{
  "id": "duolingo",
  "title": "Duolingo",
  "keywords": ["duolingo", "langue", "language", "apprendre", "learn"],
  "url": "https://www.duolingo.com/learn",
  "durationMinutes": 5
}
```

Toute entrée invalide (URL sans protocole, mots-clés vides, durée hors bornes) est
ignorée par l'application : mieux vaut une liste plus courte qu'un lien inattendu.

## Contribuer

1. Modifiez `presets.json` (tableau JSON valide, une entrée par modèle).
2. Vérifiez que chaque `id` reste unique et que les `keywords` couvrent les deux langues.
3. Ouvrez une pull request en expliquant le modèle ajouté ou corrigé.

Le format doit rester identique à la liste embarquée de l'application, afin que
Dailyz fonctionne aussi hors ligne.

---

**English TL;DR** — `dailyz-presets` is the public, read-only catalog of routine
presets consumed by the closed-source Dailyz app. It only holds `presets.json`, served
at `https://raw.githubusercontent.com/huhu123shark/dailyz-presets/main/presets.json`.
Keep every `id` unique, `keywords` searchable in French and English, and `url` on
`http(s)`. Invalid entries are discarded by the client.
