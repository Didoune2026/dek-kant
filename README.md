# Tableau de bord indicateurs

Dashboard personnel de suivi mensuel des indicateurs économiques, boursiers, énergétiques et immobiliers. Mis à jour manuellement en début de mois.

---

## Contenu du dépôt

| Fichier | Rôle |
|---|---|
| `index.html` | Dashboard web — à ouvrir dans un navigateur ou intégrer via lien |
| `indicateurs-mensuel.xlsx` | Fichier de saisie mensuelle — 28 indicateurs sur 5 ans |

---

## Mise à jour mensuelle

**En début de chaque mois**, saisir les valeurs du mois précédent dans la feuille **Données** du fichier Excel. Les cellules de saisie sont en bleu.

```bash
# Après mise à jour du fichier Excel
git add indicateurs-mensuel.xlsx
git commit -m "mise à jour [mois] [année]"
git push
```

Le dashboard se rafraîchit automatiquement à la prochaine ouverture.

---

## Indicateurs suivis

### Marchés boursiers — cours de clôture fin de mois

| Indicateur | Source | Fréquence | Où trouver |
|---|---|---|---|
| CAC 40 | Yahoo Finance | Mensuel | [finance.yahoo.com/quote/%5EFCHI](https://finance.yahoo.com/quote/%5EFCHI/) |
| Euro Stoxx 50 | Yahoo Finance | Mensuel | [finance.yahoo.com/quote/%5ESTOXX50E](https://finance.yahoo.com/quote/%5ESTOXX50E/) |
| Nasdaq Composite | Yahoo Finance | Mensuel | [finance.yahoo.com/quote/%5EIXIC](https://finance.yahoo.com/quote/%5EIXIC/) |
| Dow Jones | Yahoo Finance | Mensuel | [finance.yahoo.com/quote/%5EDJI](https://finance.yahoo.com/quote/%5EDJI/) |
| VIX | CBOE | Mensuel | [finance.yahoo.com/quote/%5EVIX](https://finance.yahoo.com/quote/%5EVIX/) |
| EUR / USD | Yahoo Finance | Mensuel | [finance.yahoo.com/quote/EURUSD=X](https://finance.yahoo.com/quote/EURUSD=X/) |
| OAT 10 ans | Banque de France | Mensuel | [webstat.banque-france.fr](https://webstat.banque-france.fr/) |
| Brent (USD/baril) | ICE | Mensuel | [finance.yahoo.com/quote/BZ=F](https://finance.yahoo.com/quote/BZ=F/) |

> Saisir le cours de clôture du dernier jour ouvré du mois.

---

### Indicateurs économiques

| Indicateur | Source | Fréquence | Où trouver | Note |
|---|---|---|---|---|
| SMIC horaire brut | Min. Travail | À chaque revalorisation | [service-public.fr](https://www.service-public.fr/particuliers/vosdroits/F2308) | Revalorisations habituelles : 1er janvier, parfois 1er mai |
| Taux directeur BCE | BCE | Par décision (~6 sem.) | [ecb.europa.eu](https://www.ecb.europa.eu/stats/policy_and_exchange_rates/key_ecb_interest_rates/) | Reporter la même valeur sur tous les mois sans changement |
| Inflation France (IPC) | INSEE | Mensuel | [insee.fr — série 001759970](https://www.insee.fr/fr/statistiques/serie/001759970) | Publication vers le 20 du mois suivant. Glissement annuel en % |
| Chômage France (BIT) | INSEE | Trimestriel | [insee.fr — série 001688526](https://www.insee.fr/fr/statistiques/serie/001688526) | Reporter la même valeur sur les 3 mois du trimestre |
| Pass Navigo mensuel | IDF Mobilités | Annuel (janvier) | [iledefrance-mobilites.fr](https://www.iledefrance-mobilites.fr/) | Tarif toutes zones |
| Baguette — prix moyen | Fédération Boulangers | Annuel | [boulangerie.org](https://www.boulangerie.org/) | Pas de prix réglementé national — moyenne constatée |
| Déficit public / PIB | INSEE / Eurostat | Annuel (mars-avril N+1) | [Eurostat — gov_10dd_edpt1](https://ec.europa.eu/eurostat/databrowser/view/gov_10dd_edpt1/) | Notification Eurostat publiée en mars/avril de l'année suivante |
| Confiance ménages INSEE | INSEE | Mensuel | [insee.fr — série 001605612](https://www.insee.fr/fr/statistiques/serie/001605612) | Index synthétique. Base 100 = moyenne long terme. < 100 = pessimisme |

---

### Énergie

| Indicateur | Source | Fréquence | Où trouver | Note |
|---|---|---|---|---|
| SMIC mensuel brut | Calculé | Automatique | — | Formule liée au SMIC horaire (× 151,67 h) — ne pas saisir |
| Tarif EDF réglementé (Base 6kVA) | CRE / EDF | Trimestriel | [cre.fr — Tarifs réglementés](https://www.cre.fr/Electricite/Marche-de-detail/Tarifs-reglementes) | Prix en €/kWh TTC. Révisions habituelles en février et août |
| Gaz naturel — prix réf. CRE | CRE | Mensuel | [cre.fr — Observatoire des prix](https://www.cre.fr/Gaz/Marche-de-detail/Observatoire-des-prix) | Le TRV gaz a été supprimé en juillet 2023. Depuis : prix de référence marché CRE en €/MWh |
| Taux Livret A | Banque de France | Semestriel (fév. et août) | [banque-france.fr](https://www.banque-france.fr/fr/publications-et-statistiques/statistiques/taux-et-cours/taux-livret-a) | Reporter la même valeur entre deux révisions |

---

### Immobilier

| Indicateur | Source | Fréquence | Où trouver | Note |
|---|---|---|---|---|
| ICC — Indice du Coût de la Construction | INSEE | Trimestriel + délai ~3 mois | [insee.fr — série 000868550](https://www.insee.fr/fr/statistiques/serie/000868550) | Reporter la même valeur sur les 3 mois du trimestre |
| ILC — Indice des Loyers Commerciaux | INSEE | Trimestriel + délai ~3 mois | [insee.fr — série 001515769](https://www.insee.fr/fr/statistiques/serie/001515769) | Base 100 = T1 2008. Plafonne les révisions de loyers commerciaux |
| ILAT — Loyers Activités Tertiaires | INSEE | Trimestriel + délai ~3 mois | [insee.fr — série 001515770](https://www.insee.fr/fr/statistiques/serie/001515770) | Base 100 = T1 2010. S'applique aux bureaux et professions libérales |
| IRL — Indice de Référence des Loyers | INSEE | Trimestriel + délai ~3 mois | [insee.fr — série 001515766](https://www.insee.fr/fr/statistiques/serie/001515766) | Base 100 = T4 2005. Plafonne les révisions de loyers résidentiels |
| Taux crédit immo moyen | Banque de France | Mensuel | [webstat.banque-france.fr](https://webstat.banque-france.fr/) ou [meilleurtaux.com](https://www.meilleurtaux.com/credit-immobilier/barometre-des-taux/) | Taux moyen toutes durées, nouveaux contrats |
| Transactions logements (12 mois) | Notaires de France | Trimestriel | [notaires.fr](https://www.notaires.fr/fr/immobilier-succession/prix-et-tendances-de-limmobilier) | Cumul 12 mois glissants, en milliers. Publication avec ~2 mois de décalage |

---

## Lecture du code couleur (fichier Excel)

| Couleur | Signification |
|---|---|
| Vert pâle | Donnée vérifiée sur source officielle |
| Jaune pâle | Estimation issue de données publiques — à vérifier |
| Violet pâle | Donnée trimestrielle répétée sur les 3 mois du trimestre |
| Bleu pâle | Formule liée à un autre indicateur — ne pas modifier |

---

## Configuration du dashboard

1. Publier ce dépôt sur GitHub (public ou privé)
2. Ouvrir `index.html` dans un navigateur
3. Cliquer sur ⚙ Réglages
4. Coller l'URL raw du fichier Excel :
   `https://raw.githubusercontent.com/[compte]/[repo]/main/indicateurs-mensuel.xlsx`
5. Cliquer OK — l'URL est mémorisée dans le navigateur

Le dashboard relit le fichier à chaque actualisation. Aucune clé API, aucun abonnement.

---

## Intégration sur un site (didoune.com)

Lien direct vers le dashboard GitHub Pages :
```
https://[compte].github.io/[repo]/
```

Pour activer GitHub Pages : Settings du dépôt › Pages › Source : branch `main`, dossier `/root`.

---

*Dernière mise à jour du fichier de données : mai 2026*
