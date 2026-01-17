# barometre-desirabilite-luxe

## Idée de départ

Un questionnement est à l’origine de ce projet. Nous vivons dans une ère où les données sont devenues une ressource clé pour les entreprises, quel que soit leur secteur d’activité. La science des données et les modèles prédictifs jouent aujourd’hui un rôle central dans la prise de décision, l’optimisation des performances et l’anticipation des comportements des consommateurs. Cependant, une question se pose lorsque l’on s’intéresse à des secteurs plus artistiques et créatifs, comme la mode ou le luxe, où les choix semblent avant tout guidés par le goût, l’émotion et la subjectivité individuelle : quelle est réellement la place de la data dans ces industries ?

C’est à partir de cette interrogation que ce projet a été pensé. Comment les marques de mode, et plus particulièrement les maisons de luxe, parviennent-elles à anticiper ce que leurs clients souhaiteront porter dans six mois, voire un an, alors même que les tendances ne sont pas encore visibles ? Comment détecter des signaux faibles, des dynamiques collectives émergentes, dans un univers où chaque individu possède ses propres préférences ?

Contrairement à la fast fashion, qui repose souvent sur une logique de réaction rapide et de reproduction de tendances déjà existantes, le luxe fait face à des contraintes différentes. Les collections sont conçues longtemps à l’avance, les volumes sont limités, et l’enjeu dépasse la simple vente : il s’agit aussi de préserver une image de marque, un storytelling et une identité créative forte.

L’objectif de ce projet n’est donc pas de prétendre prédire les goûts individuels, mais de comprendre comment les données et les outils de la science des données peuvent aider à réduire l’incertitude, éclairer les décisions stratégiques et accompagner le processus créatif dans un secteur où l’anticipation est cruciale.

---

## 1. Le choix des données : de l'ambition à la réalité

La première étape de ce projet a été de trouver un jeu de données pertinent. Ma première idée, un peu naïve, était de collecter les données directement sur les sites des grandes maisons de luxe via le web scraping. J'ai cependant vite réalisé que ces sites sont hautement sécurisés et que cette technique, que je ne maîtrisais pas encore, représentait un défi trop complexe pour un début.

Comme tout étudiant en data, je me suis alors tourné vers **Kaggle** pour trouver un dataset tabulaire. Mon choix s'est arrêté sur celui de **Vestiaire Collective**. Ce dernier est lui-même issu d'un scraping, mais il nous place face à une réalité différente : celle des produits de seconde main.

## 2. Le défi technique : l'absence d'indicateur temporel

Mon objectif de départ était de prédire les nouvelles tendances et d'identifier des signaux faibles, à l'image des départements stratégiques des maisons de luxe. Cependant, en commençant l'exploration, j'ai dû me confronter à la définition même d'une "tendance".

Pour identifier une tendance, il est indispensable de disposer d'une **évolution temporelle** (par exemple, observer la hausse des achats de produits bordeaux entre 2023 et 2024). Ma base de données ne possédant aucun indicateur temporel précis, mon idée initiale était irréalisable en l'état.

## 3. Le pivot : Construire un Score de Désirabilité

Face à cette contrainte, j'ai décidé de faire pivoter le projet : plutôt que de prédire l'avenir, j'ai choisi de mesurer le présent. J'ai eu l'idée de construire un **Score de Désirabilité**.

L'objectif est de transformer cette notion subjective en une mesure mathématique pour chaque produit, en fonction de différentes variables disponibles. Le but final est de construire un modèle prédictif de classification capable de déterminer si un nouveau produit, avec des caractéristiques spécifiques, sera "désirable" ou non, en se basant sur les comportements observés sur le marché de la seconde main.

## 4. Méthodologie : Construction mathématique du Score de Désirabilité

Pour transformer la notion subjective de "désirabilité" en une donnée quantitative exploitable, j'ai mis au point une formule de calcul pondérée :

$$Score = (0.5 \times Like_{norm}) + (0.3 \times Posts_{norm}) + (0.1 \times Color_{score}) + (0.1 \times Material_{score})$$

### Pourquoi cette pondération ?

- **Les Likes (50%)** : C'est l'indicateur le plus fort. Un "like" représente une intention d'achat ou un intérêt direct du consommateur.
- **Le volume de Posts (30%)** : La présence massive d'un type de produit indique une tendance de marché et une offre importante qui nourrit la désirabilité.
- **La Couleur et la Matière (10% chacun)** : Ce sont les fondements esthétiques. Bien que secondaires par rapport à l'engagement social, ils constituent la base du "goût" qui qualifie le produit.

Cette approche permet de classer les produits non plus sur une impression, mais sur un **indicateur composite robuste**. Ce score devient ainsi la "variable cible" que mon futur modèle de Machine Learning tentera de prédire.
