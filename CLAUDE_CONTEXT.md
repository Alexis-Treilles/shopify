# Contexte projet Camaraid — Pour Claude

## Projet

Thème Shopify pour **Camaraid** (anciennement Rocaraid) — boutique française de pièces plastiques rares et accessoires fabriqués en France pour Renault 4L, R5, R6 et motos.

---

## Git / GitHub

| Élément | Valeur |
|---|---|
| Repo | `Alexis-Treilles/shopify` |
| Branche de travail | `claude/git-modifications-MYaKk` |
| Branche avec tout le travail précédent | `amelioration-homepage` |
| Branche principale | `main` |
| PAT GitHub (actif) | ⚠️ À récupérer auprès du propriétaire du repo (token ghp_...) |

### Commandes push
```bash
# Push via PAT (git push direct bloqué par proxy)
git push https://<TON_PAT>@github.com/Alexis-Treilles/shopify.git claude/git-modifications-MYaKk
```

### Outils MCP disponibles
Les outils `mcp__github__*` sont disponibles dans cette session (via GitHub MCP server).  
**Limitation** : le token MCP ne peut pas créer de nouvelles branches (403). Utiliser le PAT ci-dessus via Bash pour le push, ou `mcp__github__push_files` sur une branche existante.

---

## Shopify

| Élément | Valeur |
|---|---|
| Nom de la boutique | Camaraid |
| Store ID (CDN) | `1/0571/7816/1213` |
| URL CDN | `https://cdn.shopify.com/s/files/1/0571/7816/1213/` |
| Thème | FullStack (custom) |

### Apps installées
| App | ID |
|---|---|
| Judge.me Reviews | `61ccd3b1-a9f2-4160-9fe9-4fec8413e5d8` |

### Metafields Judge.me (dans les templates Liquid)
```liquid
product.metafields.judgeme.all_reviews_rating.value  → note moyenne (ex: 4.71)
product.metafields.judgeme.reviews_count.value        → nombre d'avis (ex: 7)
```

---

## Klaviyo

| Élément | Valeur |
|---|---|
| API Key publique | `pk_ec8555b6fd18602d0c6047aa4b4e181bf7` |
| Activé | `true` (dans `config/settings_data.json`) |

---

## Réseaux sociaux (rebrandés Camaraid)

| Réseau | URL |
|---|---|
| Instagram | `https://www.instagram.com/camaraid/` |
| Facebook | `https://www.facebook.com/camaraid` |
| TikTok | `https://www.tiktok.com/@camaraid` |

---

## Contact

| Élément | Valeur |
|---|---|
| Email | `camaraid@gmail.com` |

---

## Fichiers modifiés (vs `main`)

| Fichier | Ce qui a changé |
|---|---|
| `config/settings_data.json` | Rebrand rocaraid→camaraid (URLs réseaux sociaux) |
| `sections/cart-drawer.liquid` | Info livraison hardcodée (4€ Relay / 7,50€ Colissimo, CSS `.camaraid-livraison-drawer`) |
| `sections/footer-group.json` | Livraison FR/BE/ES/CH, paiements, stats 80+ commandes |
| `snippets/meta-tags.liquid` | Schema.org JSON-LD avec aggregateRating Judge.me, OG tags produit |
| `templates/index.json` | H1, avis diversifiés, stats, section moto (collection `pour-moto`), badge 🇫🇷 |
| `templates/page.about.json` | Page À propos Camaraid réécrite (histoire, valeurs, 4L Trophy, CTA contact) |
| `templates/product.json` | Ordre blocs, info livraison visible, sections lorem ipsum cachées |

---

## Logistique / Livraison (à afficher partout)

- **Mondial Relay** : 4,00 € — **Gratuite dès 30 €**
- **Colissimo à domicile** : 7,50 € — Gratuite dès 45 €
- **Pays** : France · Belgique · Espagne · Suisse
- **Délai expédition** : sous 3 jours ouvrés (fabriqué à la commande)

---

## Contraintes Shopify (validations connues)

| Paramètre | Contrainte |
|---|---|
| `font_weight` | Doit être un **integer**, pas une string (`400` pas `"400"`) |
| `layout_gap_desktop` | Max **50** |
| `padding_horizontal/vertical` | Min **10** |

---

## Notes techniques

- Les fichiers `*.json` de type groupe Shopify (ex: `footer-group.json`, `cart-drawer-group.json`) commencent par un commentaire `/* ... */` à ignorer avant le JSON.
- Le cart drawer (panneau latéral) est dans `sections/cart-drawer.liquid` — **pas** `templates/cart.json` (page /cart jamais affichée).
- Le push git direct via CLI est bloqué par un proxy (403). Utiliser le PAT ou les outils MCP.
