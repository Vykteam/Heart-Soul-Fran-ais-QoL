# Pokémon Heart & Soul — version française

Traduction française de [Pokémon Heart & Soul](https://github.com/PokemonHnS-Development/pokehns-expansion)
2.0.6, le remake de Pokémon Or, Argent et Cristal (et demake de HeartGold et SoulSilver)
sur Game Boy Advance, accompagnée de quelques améliorations de confort.

> **Version bêta.** Le jeu est entièrement traduit, mais la relecture en jeu est
> encore en cours. Si vous trouvez un texte coupé, une coquille ou un bug,
> ouvrez une *issue* en précisant le lieu et la situation.

## Contenu

- Traduction française complète de HnS. Elle reprend la terminologie officielle
  de HeartGold et SoulSilver.

### Améliorations de confort

- Les CS Flash et Vol sont utilisables par n'importe quel Pokémon de l'équipe.
- Un objet clé « Repousse Infini » est ajouté.
- On peut voler depuis la carte du Pokématos.
- La Corde Sortie devient un objet clé.
- Les types sont affichés en combat.
- Le type réel des capacités à type variable (Puissance Cachée…) est affiché.
- Le clavier passe automatiquement en minuscules.
- On peut rappeler les capacités depuis le résumé du Pokémon.

Fonction déjà présente dans HnS, rappelée ici : un second objet peut être
enregistré sur Select, et s'utilise en maintenant la touche.

## Installation

Le jeu se distribue sous forme de patch. Aucune ROM n'est fournie.

1. Procurez-vous la ROM de **Pokémon Emerald Version (USA, Europe)** à partir de
   votre propre cartouche. **N'utilisez pas la version française** (Émeraude) : le
   patch ne s'appliquerait pas.
   - SHA-1 attendu : `f3ae088181bf583e55daf962a92bb46f4f1d07b7`
2. Téléchargez `Pokemon_HnS_FR.ups` dans les *assets* de la release.
3. Ouvrez [Rom Patcher JS](https://www.marcrobledo.com/RomPatcher.js/).
   Choisissez la ROM, puis le patch, et cliquez sur « Apply patch ».
4. Lancez la ROM obtenue dans votre émulateur. Commencez une **nouvelle partie** :
   les sauvegardes de la version anglaise ne sont pas garanties.

SHA-1 de la ROM patchée : `f59f3da99eb2f683c346305fdbd452b652ab1f9d`.

## Sources

Les sources sont publiées sous forme de différence avec le projet d'origine.
`Pokemon_HnS_FR_2.0.6-beta1.diff`, dans les *assets* de la release, contient toutes
les modifications de cette version : traduction, améliorations de confort et outil
du classeur des combats. Pour reconstituer les sources :

```bash
git clone https://github.com/PokemonHnS-Development/pokehns-expansion.git
cd pokehns-expansion
git checkout Release-v2.0.6
git apply ../Pokemon_HnS_FR_2.0.6-beta1.diff
make hns
```

`git apply` signale un avertissement d'espacement (« whitespace »). Il est attendu
et sans conséquence. Pour la compilation, suivez `INSTALL.md`, comme pour le projet
d'origine.

La ROM est compilée **sans** l'option `release`. Le menu de débogage (R + Start)
est donc accessible, et il est en anglais.

## Classeur des combats

`hns-combats.xlsx`, vierge, accompagne le jeu. Il compte quatre onglets, tous lus
dans les sources du jeu :

- la table des types ;
- les combats de dresseurs, avec les équipes, niveaux, objets, talents et capacités ;
- les rencontres sauvages ;
- un suivi des rencontres pour le Nuzlocke : les zones et les lignées déjà
  rencontrées s'y grisent automatiquement.

Pour le regénérer depuis les sources (Python 3.10 ou plus, avec `openpyxl`) :

```bash
make hns
python tools/hns_battles/export_xlsx.py mon-classeur.xlsx
```

`make hns` doit passer avant : il produit le fichier des équipes
(`src/data/trainers_hns.h`) que le script lit. **Sans argument, le script écrit
`hns-combats.xlsx` à la racine des sources et remplace le classeur existant**,
votre suivi compris. Indiquez donc un autre nom de fichier pour conserver votre
suivi.

## Crédits

- [Pokémon Heart & Soul](https://github.com/PokemonHnS-Development/pokehns-expansion),
  ses développeurs et contributeurs (voir `CREDITS.md` dans les sources).
- [pokeemerald-expansion](https://github.com/rh-hideout/pokeemerald-expansion) 1.15.1,
  par RHH (Rom Hacking Hideout).
- [Modern Emerald](https://github.com/resetes12/pokeemerald), par resetes12.
- [pokeemerald](https://github.com/pret/pokeemerald), le projet de décompilation de pret.

## Mention légale

Projet amateur, non commercial, sans lien avec Nintendo, Game Freak, Creatures
ou The Pokémon Company, qui détiennent les droits sur Pokémon. Aucune ROM n'est
distribuée : vous devez posséder le jeu d'origine.
