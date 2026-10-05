# 🔬 Simulateur IFREMER — Croissance des polypes coralliens

[![Version](https://img.shields.io/badge/version-6.0.0-000091?style=flat-square&logo=github)](https://github.com/gunout/simulateur-ifremer)
[![License](https://img.shields.io/badge/license-MIT-16a34a?style=flat-square)](./LICENSE)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/fr/docs/Web/JavaScript)
[![No Dependencies](https://img.shields.io/badge/dependencies-0-fbbf24?style=flat-square)](.)
[![IFREMER](https://img.shields.io/badge/data-IFREMER-000091?style=flat-square)](https://www.ifremer.fr/)
[![HYSCORES](https://img.shields.io/badge/projet-HYSCORES-E1000F?style=flat-square)](.)
[![Spectrhabent-OI](https://img.shields.io/badge/projet-Spectrhabent--OI-E1000F?style=flat-square)](.)
[![La Réunion](https://img.shields.io/badge/zone-La%20Réunion-16a34a?style=flat-square)](.)
[![Pas horaire](https://img.shields.io/badge/résolution-17%20520%20h-fbbf24?style=flat-square)](.)
[![Comparaison](https://img.shields.io/badge/comparaison-6%20max-9333ea?style=flat-square)](.)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-16a34a?style=flat-square)](.)

> Simulateur scientifique autonome de croissance des polypes coralliens — Modèle physiologique horaire basé sur les données IFREMER (projets HYSCORES et Spectrhabent-OI) de la côte ouest de La Réunion.

---

## 📖 Description

**Simulateur IFREMER** est une application web **mono-fichier** (HTML + CSS + JavaScript, **zéro dépendance**) qui modélise heure par heure la croissance de polypes coralliens sur **24 mois (17 520 pas de temps)**.

Le moteur physiologique reproduit fidèlement les mécanismes biologiques réels : **photosynthèse**, **calcification**, **nutrition hétérotrophe**, **mortalité** et **symbiose avec les zooxanthelles**. Il permet de tester virtuellement des stratégies d'élevage ou de restauration récifale et de comparer leurs effets.

L'application est livrée avec **4 secteurs récifaux intégrés** (Saint-Gilles, Saint-Leu, Étang-Salé, Saint-Pierre) dont les paramètres proviennent directement du fichier `reunion_974_analyses_completes.json` publié par l'IFREMER sur data.gouv.fr.

---

## ✨ Fonctionnalités

### 🧬 Modèle physiologique complet
- **Photosynthèse** — courbe de réponse à la lumière (optimum ~65 PAR), stress thermique, effet du pH
- **Calcification** — enrichissement en carbonates jusqu'à ×2.1, chute sous pH 7.9, optimum à 28 °C
- **Nutrition** — fréquence (optimum 2–3×/semaine) × qualité (standard / riche / très riche)
- **Mortalité** — thermique, sédimentation, compétition avec les algues, surnourrissage
- **Zooxanthelles** — ratio symbiotique dynamique modulé par la photo et le stress

### ⏱ Résolution horaire
- **17 520 pas de temps** sur 24 mois
- **Cycle jour/nuit** intégré (PAR nul la nuit, sinusoïdal le jour)
- **Variation diurne** de température (±0.8 °C) et de pH (±0.05)
- **Saisie horaire personnalisée** : tableau éditable (température, pH, PAR, nourrissage, alcalinité)
- **Événements planifiés** : nourrissage intensif, stress thermique, renouvellement d'eau, boost alcalinité

### 📁 Chargement JSON externe
Le simulateur reconnaît automatiquement **3 formats** :
1. `reunion_974_analyses_completes.json` (avec `analyses.classifications`)
2. `{ datasets: [...] }` avec `corail_surface_km2`
3. `{ "secteur": {...}, ... }` objet de secteurs direct

Les secteurs importés **fusionnent** avec les 4 intégrés. Un bouton de restauration permet de revenir à l'état initial.

### ⚖️ Comparaison multi-simulations
- **Jusqu'à 6 simulations** sauvegardées en mémoire
- **Cartes côte à côte** (meilleur 🏆 / pire ⚠️)
- **Tableau comparatif** avec surlignage des meilleures/pires valeurs
- **Graphique superposé** : simulations sauvegardées en pointillés colorés

### 📥 Exports multiples

| Format | Contenu |
|---|---|
| **CSV** | Simulation active (indicateurs, paramètres, résultats) |
| **JSON** | Données complètes + simulations sauvegardées |
| **Rapport HTML** | Charte tricolore officielle, inclut la comparaison |
| **CSV Comparaison** | Toutes les simulations côte à côte |

### 🎨 Design institutionnel
- **Charte État français** : bandeau tricolore, Marianne RF, palette `#000091` / `#E1000F` / `#fbbf24`
- **Thème clair/sombre** persistant via `localStorage`
- **Responsive** : sidebar rétractable sur mobile
- **Typographie** : Marianne (fallback system-ui) + mono pour les valeurs

---

## 🚀 Utilisation

### Installation

**Aucune installation requise.** Le simulateur est un fichier HTML autonome.

1. **Clonez** le dépôt : `git clone https://github.com/gunout/simulateur-ifremer.git`
2. **Ouvrez** `simulateur-polypes-v6.html` dans Chrome / Firefox / Safari
3. C'est prêt ✅

Aucune connexion internet, aucun serveur, aucune dépendance npm.

### Démarrage rapide

1. Ouvrez le fichier HTML dans votre navigateur.
2. Ajustez les paramètres dans la barre latérale gauche.
3. Choisissez un secteur récifal (Saint-Gilles, Saint-Leu, Étang-Salé, Saint-Pierre).
4. Cliquez sur **▶ LANCER LA SIMULATION**.
5. Observez les KPI en haut et les graphiques.
6. Cliquez sur **💾 Sauvegarder pour comparaison**.
7. Répétez avec d'autres réglages.
8. Ouvrez l'onglet **⚖️ Comparer** pour visualiser toutes les simulations.
9. Exportez via les boutons en bas (CSV, JSON, HTML, Comparaison).

### Paramètres disponibles

| Paramètre | Plage | Optimum | Effet |
|---|---|---|---|
| **Fréquence de nourrissage** | 0 – 7 /sem | 2 – 3 | ↑ nutrition jusqu'à saturation |
| **Qualité nutritionnelle** | Standard / Riche / Très riche | Riche | ×1.25 à ×1.48 |
| **Alcalinité** | +0 – +100 % | +50 – +100 % | ↑ calcification jusqu'à ×2.1 |
| **Température** | 22 – 32 °C | 26 – 27 °C | stress > 30 °C |
| **pH** | 7.6 – 8.4 | 8.1 – 8.2 | chute calcification < 7.9 |
| **Intensité lumineuse** | 0 – 100 | 60 – 80 | optimum photosynthèse |
| **Brouteurs** | 0 – 100 | > 70 | ↓ compétition algues |
| **Sédimentation** | 0 – 100 | < 30 | ↓ mortalité |

### Charger un JSON externe

1. Glissez votre fichier JSON dans la zone 📁 en haut à gauche.
2. Ou cliquez pour ouvrir un sélecteur de fichier.
3. Les secteurs reconnus sont **fusionnés** avec les 4 intégrés.
4. Le compteur **SECTEURS** en haut à droite se met à jour.
5. Le panneau **SOURCE** indique le nom du fichier importé.

---

## 📊 Indicateurs calculés

| Indicateur | Unité | Description |
|---|---|---|
| **Croissance nette** | %/an | Taux annuel de croissance de la surface corallienne |
| **VCH** | 0–100 | Vitalité Corallienne Hyperspectrale |
| **Polypes** | millions | Densité estimée de polypes (1 ind./cm²) |
| **Mortalité** | %/h | Taux horaire moyen (thermique, sédimentation, algues) |
| **Ratio zooxanthelles** | 0–1.3 | Densité symbiotique |
| **Surface corallienne** | km² | Surface de corail vivant |

---

## ⚠️ Incertitudes documentées

| Source | Amplitude | Impact |
|---|---|---|
| **Décote marégraphique 2015** | ±15 points VCH | Sous-estimation possible |
| **Géoréférencement** | ±10 % longueur | Faux positifs de changement |
| **Seuils VCH** | Non publiés | Classification discutable |
| **Licence** | notspecified | Usage juridique incertain |
| **Validation terrain 2015** | Absente | Uniquement 2009-2010 |

### Précautions d'interprétation

- ❌ Ne pas attribuer causalement sans contrôle des covariables
- ❌ Ne pas interpréter ΔVCH > +70 % comme « restauration réussie »
- ❌ Ne pas utiliser VCH comme indicateur unique de conformité DCE
- ✅ Toujours mentionner les incertitudes dans tout rapport
- ✅ Toujours croiser avec d'autres indicateurs (DCE I, CORRAM)

---

## 📚 Sources scientifiques

- **IFREMER** — Institut français de recherche pour l'exploitation de la mer
- **HYSCORES** (2015–2016) — Projet hyperspectral Ifremer/UBO/Office de l'Eau Réunion
- **Spectrhabent-OI** (2009–2012) — Projet IFREMER/UBO
- **data.gouv.fr** — 13 datasets récifs ouest Réunion
- **Référence de croissance de base** : 0.52 %/an (données IFREMER 2009-2015)

---

## 📂 Structure du dépôt

    simulateur-ifremer/
    ├── README.md
    ├── LICENSE
    ├── simulateur-polypes-v6.html     # Application mono-fichier
    ├── data/
    │   └── reunion_974_analyses_completes.json
    └── docs/
        └── captures/                  # Captures d'écran

---

## 🛠 Architecture technique

Le simulateur est un fichier HTML unique d'environ 2000 lignes, organisé ainsi :

    simulateur-polypes-v6.html
    ├── <style>        Charte État français + thème clair/sombre
    ├── <body>         Structure : header → topbar → app (3 colonnes)
    │   ├── sidebar    Paramètres + drop-zone JSON + simulation
    │   ├── center     7 vues à onglets + KPI + exports
    │   └── right      Panneau Intelligence Polypes + journal
    └── <script>       Moteur physiologique + UI + exports
        ├── SECTORS          Données intégrées (4 secteurs)
        ├── computeHourly    Physiologie horaire
        ├── buildProfile     Profil 17 520 pas
        ├── simulateHourly   Simulation complète
        ├── drawVCHChart     Rendu canvas (VCH + comparaison)
        ├── drawHourlyChart  Profil 72 h (temp, PAR, nourrissage)
        ├── loadExternalJSON Import JSON multi-format
        ├── renderCompare    Comparaison multi-simulations
        └── export{CSV,JSON,HTML,Comparison}

**Aucune dépendance externe** : pas de framework, pas de CDN, pas de bibliothèque graphique. Canvas 2D natif pour les graphiques.

---

## 🌐 Compatibilité

| Navigateur | Version minimale |
|---|---|
| Chrome / Edge | 90+ |
| Firefox | 88+ |
| Safari | 14+ |
| Opera | 76+ |

Fonctionne **hors-ligne** et depuis un simple `file://` — pas besoin de serveur web.

---

## 📄 Licence

Le **code du simulateur** est distribué sous licence **MIT**.

Les **données sources** (IFREMER / HYSCORES / Spectrhabent-OI) sont publiées sous licence `notspecified` — voir les conditions sur [data.gouv.fr](https://www.data.gouv.fr).

---

## 🤝 Contribution

Les contributions sont bienvenues :

1. Forkez le projet : https://github.com/gunout/simulateur-ifremer/fork
2. Créez une branche : `git checkout -b feature/nouvelle-fonctionnalite`
3. Committez : `git commit -m 'Ajout de ...'`
4. Pushez : `git push origin feature/nouvelle-fonctionnalite`
5. Ouvrez une Pull Request

### Idées d'amélioration

- [ ] Export PDF du rapport
- [ ] Intégration de covariables (profondeur, hydrodynamisme)
- [ ] Import de séries temporelles in-situ (HOBO, Sondes)
- [ ] Modèle 3D de croissance par patch
- [ ] Mode multi-secteurs simultané

---

## 📞 Contact

- **Dépôt** : https://github.com/gunout/simulateur-ifremer
- **Issues** : https://github.com/gunout/simulateur-ifremer/issues
- **IFREMER** : [ifremer.fr](https://www.ifremer.fr)

---

<div align="center">

**🇫🇷 Liberté · Égalité · Fraternité**

*Simulateur IFREMER v6.0 — HYSCORES / Spectrhabent-OI*

[![Made in La Réunion](https://img.shields.io/badge/Made%20in-La%20Réunion-16a34a?style=for-the-badge)](https://github.com/gunout/simulateur-ifremer)
[![Data IFREMER](https://img.shields.io/badge/Data-IFREMER-000091?style=for-the-badge)](https://www.ifremer.fr/)
[![Zero Dependency](https://img.shields.io/badge/Zero-Dependency-fbbf24?style=for-the-badge)](https://github.com/gunout/simulateur-ifremer)

</div>

---

<div align="center">

### 🇫🇷 Gunout · 2026

![Made in France](https://img.shields.io/badge/Made_in-France-002395?style=flat-square&labelColor=FFFFFF&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA5MDAgNjAwIj48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjYwMCIgZmlsbD0iIzAwMjM5NSIvPjxyZWN0IHdpZHRoPSI5MDAiIGhlaWdodD0iNDAwIiB5PSIxMDAiIGZpbGw9IiNmZmYiLz48cmVjdCB3aWR0aD0iOTAwIiBoZWlnaHQ9IjIwMCIgeT0iNDAwIiBmaWxsPSIjZWQyOTM5Ii8+PC9zdmc+)
![GitHub](https://img.shields.io/badge/GitHub-gunout-181717?style=flat-square&logo=github&logoColor=white)
![Year](https://img.shields.io/badge/2026-ED2939?style=flat-square&labelColor=FFFFFF)

<sub>© 2026 <strong>Gunout</strong> — Tous droits réservés.</sub>

</div>
