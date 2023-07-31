# energie_2021_France
Consommation d'énergie - électricité et gaz naturel - en 2021 à l'échelle des intercommunalités

Introduction
------------


La loi de transition énergétique pour la croissance verte”du 17 août 2015 confère aux collectivités territoriales un rôle clef dans la transition énergétique : ”En particulier, les collectivités ont la responsabilité de la planification (spécialement à l’échelle régionale) et de l’animation (spécialement à l’échelle intercommunale) de la transition énergétique “ ( citation extraite de  www.ecologie.gouv.fr/action-des-territoires-transition-energetique )

Nous nous proposons d’analyser les consommations d’énergie - électricité et gaz naturelle - à l’échelle des intercommunalités ,et de visualiser les contrastes entre les différents territoires

Sources
-------

*Consommation d’énergie , électricité et gaz naturel:* 

Les données sont téléchargées à partir du site : www.data.gouv.fr/fr/datasets/consommation-annuelle-delectricite-et-gaz-par-iris-et-par-secteur-dactivite/#/resources

Il s’agit des données collectées par l’agence ORE qui regroupe tous les acteurs de la distribution d’électricité et de gaz en France (plus de 125 entités) www.agenceore.fr

On dispose par opérateur et type d’énergie - électricité ou gaz naturel - des consommations relevées aux points de distributions à la maille “iris” , maille de découpage des communes , découpage identique à celui du recensement de la population. Les consommations sont réparties sur quatre secteurs d'activité: résidentiel , tertiaire, industriel et agricole . Pour les trois derniers, la répartition par secteur se fait sur la base des codes NAF des entreprises servies ( Le code NAF (nomenclature d’activité française) est un code délivré par l’Insee qui régit chaque activité professionnelle , identique à code APE )

Dans la version téléchargée début juillet 2023 , la dernière année complète de données est 2021.


*Intercommunalités:*

La base des intercommunalités prise en compte est la dernière version  de l’ Insee mise à jour en 2023  Intercommunalité | Insee .

Les intercommunalités sont de quatre natures: CC communautés de communes , CA communautés d'agglomérations , CU communautés urbaines CA et ME métropoles  .La métropole de Lyon , qui originellement a sa propre catégorie  METLYON , a été ajoutée à la liste ME. Le nombre d’intercommunalité est de 1231 ( France métropolitaine) .

Les contours des intercommunalités pour les cartes sont obtenues en deux temps :
    - agrégation des contours détaillés des communes , version 2022 ( source IGN :Contours Communes France Administrative "Format Admin-Express" avec arrondissements (com-fr-all-wgs84) - data.gouv.fr)  [ méthode dissolve de GeoPandas]
    - simplification des contours pour alléger les cartes [ méthode simplify de GeoPandas avec les paramètres tolerance=0.01et preserve_topology=True ]

Les populations des intercommunalités sont obtenues à partir des populations légales des communes Populations légales 2019 | Insee [ citation : “Les données de population au 1er janvier 2019 dans les limites territoriales des communes au 1er janvier 2021 sont officielles et authentifiées par le décret n° 2021-1946 du 31 décembre 2021.Ces populations entrent en vigueur au 1er janvier 2022.”] . Le recensement prévu en 2021 n’a pas eu lieu à cause du covid.


Préparation des données
-----------------------

Les données d’énergie 2021 sont agrégées à la maille commune , puis à la maille intercommunale après croisement avec le fichier des intercommunalités décrit plus haut . La répartition des consommations des énergies est donc faite sur les intercommunalités actuelles.

Résultats de l'analyse de données
---------------------------------

Les variables utilisées , que ce soit les variables de  base  , consommations d’ énergie totale ou par secteur , populations des intercommunalités ou les variables dérivées ,consommation d’énergie par habitant - n’ont pas des distributions normales.On présentera plus en détail la distribution des deux variables consommation d’énergie par habitant du secteur résidentiel et consommation d’énergie par habitant du secteur industriel.

**1-Consommation d’énergie totale (électricité et gaz naturel) [ [énergie_graphe_2]**

La somme des consommations des intercommunalités est de 901 Twh pour 2021.
Si on se réfère au bilan énergétique de 2022 publié par le ministère de l'écologie
(www.statistiques.developpement-durable.gouv.fr/edition-numerique/chiffres-cles-energie-2022/) on s’attendrait à trouver un total de 905 Twh (433 électricité et 472 gaz naturel) . A noter que le rapport du ministère  explicite un secteur transports alors que dans la base de donnée des distributeurs les transports ferroviaires sont comptabilisés dans le secteur tertiaire . L’écart correspond à 0.44% du total .

Les trois principaux secteurs de consommation sont : 40% industriel , 34% résidentiel et 25% tertiaire .La consommation du secteur agricole est faible , mais il faut bien sûr garder à l’esprit que l’électricité et le gaz naturel ne représentent qu’une faible proportion de la consommation de ce secteur ( 10 TWh par rapport à 52 TWh )

**2-Répartition par secteur de consommation selon la nature d’intercommunalité**

Les consommations moyennes , tous secteurs , sont fortement dépendantes de la nature de l’intercommunalité  [énergie_graphe_3] : de 281 GWh pour les CC à 11300 GWh en moyenne pour les ME .

La répartition par secteur de consommation diffère également  [énergie_graphe_4].
Statistiquement l’effet de la nature d’intercommunalité est fort pour les secteurs tertiaire et agricole , moins marqué pour le secteur résidentiel et faible pour le secteur industriel  [énergie_tabl1]


% secteur tertiaire : cette fois ci les CU et les ME  sont très en dessus  de la moyenne avec 30 à 32 % à comparer à 25% 
% secteur agricole : les communautés de communes avec 3.1 % sont très au dessus de la moyenne de 1.1 % .
% secteur résidentiel : les communautés de commune avec 46% sont nettement au dessus de la moyenne de 34 % .
% secteur industriel : les CU présentent une moyenne plus élevée que les autres intercommunalités mais avec une forte dispersion , qui ne permet pas de conclure.


**3-Relation entre consommation et  population des intercommunalités**

Les écarts entre nature d’intercommunalités pour la consommation totale ou la répartition par secteur incite à regarder la relation  avec la population , considérée comme la première caractéristique des intercommunalités  (cf définition des intercommunalités)  [énergie_graphe_5]

On trouve une forte corrélation entre consommation totale , consommation résidentielle et consommation tertiaire et population  [énergie_tabl2] .

Dans le détail:
secteur résidentiel [énergie_graphe_6] : la relation entre consommation résidentielle et population est linéaire pour les quatre natures d'intercommunalités . Les pentes sont égales pour CC et CA (0.0049)  et pour CU et ME (0.0042) . Il y a un écart entre les deux groupes. 

secteur tertiaire [énergie_graphe_7] : la situation est différente du cas précédent bien que l’on trouve globalement une relation entre consommation et population .
 Deux cas extrêmes : 
ME pour  laquelle on trouve une relation linéaire du même type que pour le secteur résidentiel, 
CU pour laquelle la corrélation n’est pas significative à cause du cas CU Le Havre Seine Métropole . Le recoupement avec des informations détaillées montre que c’est dû à la Zone Industrielle Portuaire de Gonfreville l’Orcher ( on rappelle que toutes les activités de transport , fret et services aux entreprises sont dans le secteur tertiaire )

Pour CC et CA on trouve une situation intermédiaire avec des points exceptionnels , dont l’origine n’ a pas été cernée ici , et de la dispersion se traduisant par une moins bonne détermination de la pente.
             



**4- Consommations par habitant**

*4-1 Description*

A partir des observations  précédentes, il paraît intéressant de rapporter l’énergie consommée à la population de manière à neutraliser ou décorréler certains effets. On construit donc des ratios de consommation par habitant en MWh/hab. pour le total et par secteur.

Les constats statistiques sur ces ratios 
décorrélation effective avec la population  [énergie_tabl4]
corrélation très marquée entre consommation par habitant totale et consommation par habitant du secteur industriel  [énergie_tabl5] [énergie_graphe_8]
des distributions non “normales” : les moyennes sont très différentes des médianes et les valeurs maximales sont bien au-delà du troisième quartile .Dans  les deux cas de la consommation totale et de la consommation secteur industriel  les valeurs maximales sont proches de 200 MWh/hab quand les médianes sont respectivement de 10 et 2 MWh/hab .

Pour illustrer ce dernier point , on a examiné plus en détail les distributions des ratios du secteur résidentiel ,qui paraît presque “normal” et du secteur industriel qui ne l’est pas de manière évidente.La méthodologie consiste à proposer une série de modèles de distributions possibles , à identifier le modèle donnant le meilleur accord [méthode fit de scipy.stats] puis à pratiquer un test de Kolmogorov-Smirnov (KS) pour décider si on accepte ce modèle.La liste proposée est : norm,lognorm ,genlogistic,pareto , genpareto ,weibull_min.
consommation par habitant du secteur résidentiel : le meilleur modèle est une distribution genlogistic  [logistic généralisée énergie_graphe_9] .On a également effectué le test KS avec un modèle normal , qui confirme que ce n’est pas acceptable.
consommation par accident du secteur industriel : le meilleur modèle est une distribution lognorm [lognormale énergie_graphe_10]
Ces lois prennent en compte les queues de distribution.


*4-2 Cartes*

On propose 5 cartes de France découpées à l’échelle des intercommunalités , avec une discrétisation des consommations par habitant , traduite en une échelle de couleurs, qui prend en compte dans chaque cas les particularités de la distribution.
 [énergie_graphe_11] [énergie_graphe_12] [énergie_graphe_13] [énergie_graphe_14]



**5-En conclusion à ce stade**

les intercommunalités dont la consommation totale et d’électricité se différencie le plus de la moyenne sont celles dont la consommation du secteur industriel est la plus élevée
