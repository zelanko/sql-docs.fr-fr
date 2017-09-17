---
title: "Mis à jour - Advanced Analytique des documents de SQL Server | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié dans, pour avancée d’Analytique pour Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: advanced-analytics
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: fb6185aae04a1fb53a4db03cbab267e3f52dc779
ms.contentlocale: fr-fr
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nouveaux et mis à jour récemment : Advanced Analytique pour SQL Server



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Plage de dates de mises à jour :* &nbsp; **2017-07-18** &nbsp; - à - &nbsp; **2017-09-11.**
- *Zone de sujet :* &nbsp; **avancées d’Analytique pour SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants atteindre de nouveaux articles qui ont été ajoutées récemment.


1. [Comment effectuer le calcul de score en temps réel ou calculer les scores natif dans SQL Server](r/how-to-do-realtime-scoring.md)
2. [Installer préformé d’apprentissage des modèles sur SQL Server](r/install-pretrained-models-sql-server.md)
3. [Calcul de score en natif](sql-native-scoring.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits de mises à jour collectées à partir des articles qui ont récemment subi une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriées dans la section extraits.

1. [Configurer les Python Machine Learning Services (de-de base de données)](#TitleNum_1)
2. [Présentation de revoscalepy](#TitleNum_2)
3. [Différences dans les fonctionnalités de Machine Learning entre les éditions de SQL Server](#TitleNum_3)
4. [Opérationaliser le code de R (Machine Learning Services)](#TitleNum_4)
5. [Performances pour R Services : résultats et des ressources](#TitleNum_5)
6. [Performances pour R Services - optimisation des données](#TitleNum_6)
7. [Gestion des packages R pour SQL Server](#TitleNum_7)
8. [Configurer SQL Server Machine Learning Services (en base de données)](#TitleNum_8)
9. [Configuration de SQL Server pour une utilisation avec R](#TitleNum_9)
10. [Réglage des performances pour R dans SQL Server](#TitleNum_10)
11. [Scénarios de science des données et modèles de solutions](#TitleNum_11)
12. [Quelles sont les nouveautés dans Machine Learning Services dans SQL Server](#TitleNum_12)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-set-up-python-machine-learning-services-in-databasepythonsetup-python-machine-learning-servicesmd"></a>1. &nbsp;[Configurer Python Machine Learning Services (de-de base de données)](python/setup-python-machine-learning-services.md)

*Mise à jour : 2017-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([suivant](#TitleNum_2))

<!-- Source markdown line 263.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 fbe2ef55a5caecd64bb21ce854617a10b2d65567 8cd65baf77f27db00a0a4f07f3129a4231edb48b  (PR=3084  ,  Filename=setup-python-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=05976158e43d7dfafaf02289462d1537f5beeb36) -->



     [Modify the user account pool for SQL Server R Services--../r/modify-the-user-account-pool-for-sql-server-r-services.md)

Si vous utilisez SQL Server Standard Edition et n’avez pas le gouverneur de ressources, vous pouvez utiliser les événements étendus et les vues de gestion dynamique pour vous aider à gérer les ressources du serveur. Vous pouvez également utiliser l’analyse des événements Windows à cet effet. Pour plus d’informations, consultez [surveillance et de gestion R Services--... /r/Managing-and-Monitoring-r-solutions.MD).

**Mettre à niveau les composants d’apprentissage automatique**


Lorsque vous installez les Services de Machine Learning à l’aide de SQL Server 2017, vous obtiendrez la version des composants au moment de que la publication de la mise en production. Chaque fois que des correctifs ou de la mise à niveau de l’instance de SQL Server, les composants d’apprentissage machine sont mis à niveau ainsi.

Vous pouvez mettre à niveau les composants sur une planification plus rapide qu’est pris en charge d’apprentissage automatique par les versions de SQL Server en installant Microsoft Machine Learning Server. Lorsque vous procédez ainsi, vous obtenez également des nouvelles fonctionnalités prises en charge dans la dernière version de la Machine Learning serveur, telles que :

+ Mises à jour des packages Python pour [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml pour Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).
+ [Modèles de pretrained](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) pour l’analyse de texte et de classification d’image.

Pour plus d’informations sur la façon de mettre à niveau une instance, consultez [R de mise à niveau des composants via liaison--... \r\use-sqlbindr-exe-to-upgrade-an-instance-of-SQL-Server.MD).

> [!NOTE]
>
> La version actuelle contient la version la plus récente de tous les composants d’apprentissage machine. Par conséquent, bien que les mises à jour via Microsoft Machine Learning Server sont prises en charge pour SQL Server 2017, la mise à niveau n’est actuellement disponible s’applique uniquement aux instances de SQL Server 2016.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-introducing-revoscalepypythonwhat-is-revoscalepymd"></a>2. &nbsp;[Revoscalepy de présentation](python/what-is-revoscalepy.md)

*Mise à jour : 2017-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1) | [suivant](#TitleNum_3))

<!-- Source markdown line 79.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 33f4e0e2421fa79fc11931dc7f29bff4432c6f5a d2eac3313a74bc5d5afd754fc357b3693e6801e1  (PR=2939  ,  Filename=what-is-revoscalepy.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



| (column_1) | (Colonne_2) | (column_3) |
| :-- | :-- | :-- |
|`rx_btrees` | Ajuster les arbres de décision augmentés de gradient stochastique|`rx_btrees_ex`dans CTP 2.0|
|`rx_dforest` | Ajuster les forêts décisionnelles classification et de régression|`rx_dforest_ex`dans CTP 2.0|
|`rx_dtree` | Arbres de classification et de régression adaptés |`rx_dtree_ex`dans CTP 2.0|
|`rx_lin_mod` | Créer un modèle linéaire|`rx_lin_mod_ex`dans CTP 2.0|
|`rx_logit` | Créer un modèle de régression logistique|`rx_logit_ex`dans CTP 2.0|
|`rx_predict` | Générer des prédictions à partir d’un modèle formé|`rx_predict_ex`dans CTP 2.0|
|`rx_summary` | Générer un résumé du modèle||

Nouveaux algorithmes d’apprentissage automatique sont également fournies par la version Python de [MicrosoftML](https://docs.microsoft.com/en-us/r-server/python-reference/microsoftml/microsoftml-package):

| Fonction|  Description|
| ------ | ------ |
|`rx_fast_forest` |Créez un modèle de forêt de décision|
|`rx_fast_linear` | Régression linéaire avec élévation de coordonnées double stochastique|
|`rx_fast_trees` | Créer un modèle d’arbre augmenté |
|`rx_logistic_regression` | Créer un modèle de régression logistique|
|`rx_neural_network` | Créer un modèle de réseau neuronal personnalisable |
|`rx_oneclass_svm` | Crée un modèle SVM sur un jeu de données déséquilibré, pour la détection d’anomalie|

> [!TIP]
> La plupart de ces algorithmes sont déjà fournies sous forme de modules dans Azure Machine Learning.

MicrosoftML pour Python inclut également des transformations et les fonctions d’assistance, telles que :

+ `rx_predict`génère des prédictions à partir d’un modèle formé et peut être utilisé pour calculer les scores en temps réel
+ fonctions de la personnalisation d’image
+ fonctions d’extraction de traitement et l’opinion de texte

Pour plus d’informations, consultez [présentation MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)


> [!NOTE]
> La Communauté Python utilise les conventions de codage qui peuvent être différentes de celui que vous êtes habitué, y compris toutes les lettres minuscules et des traits de soulignement au lieu de casse mixte pour les noms de paramètre. En outre, peut-être que vous avez remarqué que la **revoscalepy** bibliothèque est toujours en minuscule. C'est juste ! Une autre convention Python.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-differences-in-machine-learning-features-between-editions-of-sql-serverrdifferences-in-r-features-between-editions-of-sql-servermd"></a>3. &nbsp;[Différences de fonctionnalités de machine learning entre les éditions de SQL Server](r/differences-in-r-features-between-editions-of-sql-server.md)

*Mise à jour : 2017-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_2) | [suivant](#TitleNum_4))

<!-- Source markdown line 47.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5890e212063f3ef228e69afe54e226320d2467f 4e0357701d960c0b8dbda1ac8d56a82f3335c77f  (PR=2964  ,  Filename=differences-in-r-features-between-editions-of-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=7b4f037616e0559ac62bbae5dbe04aeffe529b06) -->



     Only Express Edition with Advanced Services includes the machine learning features. The performance limitations are similar to Standard Edition. Web edition is not intended for tasks such as creating machine learning models; however, you can use the PREDICT function to perform scoring using models trained elsewhere.

-   **Azure SQL Database**

     Fonctionnalités de la machine learning tels que R et Python de script ne sont pas actuellement pris en charge dans la base de données SQL Azure.

     Pour plus d’informations et des annonces relatives lorsque cette fonctionnalité sera disponible, consultez le blog de SQL Server : [Python dans SQL Server 2017 : amélioré dans base de données d’apprentissage](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)


**Langues prises en charge dans toutes les éditions**


Les langues d’apprentissage machine suivantes sont prises en charge pour toutes les éditions :

+ SQL Server 2017 : R et Python
+ SQL Server 2016 : R uniquement

Microsoft R Open est fourni avec toutes les éditions.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-operationalize-r-code-machine-learning-servicesroperationalizing-your-r-codemd"></a>4. &nbsp;[Le code R de tiens (Machine Learning Services)](r/operationalizing-your-r-code.md)

*Mise à jour : 2017-07-27* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_3) | [suivant](#TitleNum_5))

<!-- Source markdown line 56.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7e11d9a5db93932ec89ca96b5337aa4ea03c1d13 0779f06444b5b73ae2dff8bc190d0e388b4ae8e7  (PR=2660  ,  Filename=operationalizing-your-r-code.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=70a1fd4dbec68d22187585de69a1d603c39e259e) -->



+ [En temps réel :... / real-time-scoring.md) de calcul de score, optimisé pour les lots de petite taille
+ Calcul de score, appelé à partir d’une application de ligne unique
+ [Natif score--... / sql-natif-scoring.md), pour la prédiction de traitement rapide de SQL Server sans appeler R

Cette procédure pas à pas fournit des exemples de calcul de score à l’aide d’une procédure stockée dans le lot et les modes de ligne unique :

+ [Bout en bout de procédure pas à pas de données scientifiques de R dans SQL Server--... / tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Consultez ces modèles de solution pour obtenir des exemples montrant comment intégrer le calcul de score dans une application :

+ [Prévisions de vente au détail](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Détection des fraudes](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)
+ [Client de gestion de clusters](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

**Améliorer les performances et l’échelle**


Bien que le langage R open source connu pour avoir des limitations, le package RevoScaleR API peut opérer sur les jeux de données volumineux et tirer parti des calculs dans la base de données multicœurs, multithreads et multiprocessus.

Si votre solution R utilise des agrégations complexes ou implique des jeux de données volumineux, vous pouvez tirer parti des agrégations en mémoire très efficaces de SQL Server et les index columnstore et laisser le code R les calculs statistiques et de calcul de score.

Pour plus d’informations sur la façon d’améliorer les performances dans l’apprentissage de SQL Server, consultez :

+ [Réglage des performances pour SQL Server R Services--... /.. / advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Conseils et astuces de l’optimisation des performances](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Adapter le code R pour d’autres plateformes ou contextes de calcul**




&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-performance-for-r-services-results-and-resourcesrperformance-case-study-r-servicesmd"></a>5. &nbsp;[Performances pour R Services : résultats et des ressources](r/performance-case-study-r-services.md)

*Mise à jour : 2017-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_4) | [suivant](#TitleNum_6))

<!-- Source markdown line 282.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 40c8cd255ead88edc60531d45dd0377ecbaf7c9b eeca5eed96e2223508910b246dbff18173eecea3  (PR=2565  ,  Filename=performance-case-study-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



Les packages MicrosoftML et RevoScaleR ont été utilisés pour l’apprentissage d’un modèle de prévision dans une solution R complexe impliquant de volumineux datasets. Requêtes SQL et le code R étaient identiques. Tous les tests ont été effectués sur une seule machine virtuelle de Azure avec SQL Server est installé. Ensuite, l’auteur comparé heures de calcul de score avec et sans ces optimisations fournies par SQL Server :

- Tables en mémoire
- Soft-NUMA
- Resource Governor

Pour évaluer l’effet de soft-NUMA sur l’exécution du script R, l’équipe de science des données testé la solution sur une machine virtuelle Azure avec 20 cœurs physiques. Sur ces cœurs physiques, les quatre nœuds soft-NUMA ont été créées automatiquement, telle que chaque nœud contenus cinq cœurs.

Affinage de l’UC a été appliqué dans le scénario de mise en correspondance de reprise, afin d’évaluer l’impact sur les travaux R. Quatre **pools de ressources SQL** et quatre **pools de ressources externes** ont été créés, et l’affinité du processeur a été spécifiée pour vous assurer que le même jeu de processeurs est utilisable dans chaque nœud.

Chacun des pools de ressources a été attribué à un groupe de charges de travail différent, pour optimiser l’utilisation du matériel. La raison est que Soft-NUMA et l’affinité de processeur ne peut pas diviser la mémoire physique dans les nœuds NUMA physiques ; Par conséquent, par définition, tous les nœuds NUMA logicielles qui sont basés sur le même nœud NUMA physique doivent utiliser mémoire dans le même bloc de mémoire du système d’exploitation. En d’autres termes, il n’existe aucune affinité du processeur de mémoire.

Le processus suivant a été utilisé pour créer cette configuration :

1. Réduire la quantité de mémoire allouée par défaut pour SQL Server.

2. Créez quatre nouveaux pools pour exécuter les travaux R en parallèle.

3. Créez quatre groupes de charges de travail de sorte que chaque groupe de charge de travail est associé à un pool de ressources.

4. Redémarrez le gouverneur de ressources avec les nouveaux groupes de charges de travail et les affectations.

5. Créer une fonction classifieur définie par l’utilisateur (UDF) permettent d’attribuer différentes tâches sur les groupes de charges de travail différent.

6. Mettre à jour la configuration du gouverneur de ressources pour utiliser la fonction pour les groupes de charges de travail approprié.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-performance-for-r-services---data-optimizationrr-and-data-optimization-r-servicesmd"></a>6. &nbsp;[Performances pour R Services - optimisation des données](r/r-and-data-optimization-r-services.md)

*Mise à jour : 2017-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_5) | [suivant](#TitleNum_7))

<!-- Source markdown line 107.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2ae2e54e8c5c8a3ec92fd2017088dd6ee879a9a1 9cb06bdce4ad6dfa2e9dc19da49103a6cd9817b3  (PR=2565  ,  Filename=r-and-data-optimization-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



> Si une table est spécifiée dans la source de données au lieu d’une requête, R Services utilise l’heuristique interne pour déterminer les colonnes nécessaires pour récupérer à partir de la table ; Toutefois, cette approche est peu susceptible d’engendrer l’exécution en parallèle.

Pour vous assurer que les données peuvent être analysées en parallèle, la requête utilisée pour récupérer les données doit être encadrée de telle sorte que le moteur de base de données peut créer un plan de requête parallèle. Si le code ou l’algorithme utilise des volumes importants de données, assurez-vous que la requête donnée à `RxSqlServerData` est optimisé pour une exécution parallèle. Une requête qui ne retourne pas de plan d’exécution parallèle peut générer un processus unique pour le calcul.

Si vous avez besoin travailler avec les jeux de données volumineux, utilisez Management Studio ou un autre analyseur de requêtes SQL avant d’exécuter votre code R, pour analyser le plan d’exécution. Effectuer toutes les étapes recommandées pour améliorer les performances de la requête. Par exemple, l’absence d’un index sur une table peut faire augmenter le temps d’exécution d’une requête. Pour plus d’informations, consultez [surveillance et le réglage des performances--.. /.. / relational-databases/performance/monitor-and-tune-for-performance.md).

Une autre erreur courante qui peut affecter les performances est une requête extrait des colonnes supplémentaires que nécessaire. Par exemple, si une formule est basée sur seulement trois colonnes, mais il se peut que votre table source a 30 colonnes, vous déplacez données inutilement.

 + Évitez d’utiliser `SELECT *`!
 + Prendre un certain temps pour vérifier les colonnes dans le jeu de données et identifier uniquement ceux qui sont nécessaires pour l’analyse
 + Supprimer à partir de vos requêtes, toutes les colonnes qui contiennent des types de données qui ne sont pas compatibles avec le code R, tels que les GUID et ROWGUID
 + Vérification des formats non pris en charge de date et heure
 + Plutôt que de charger une table, créez une vue qui sélectionne certaines valeurs ou convertit les colonnes pour éviter les erreurs de conversion

**Optimisation de l’algorithme d’apprentissage automatique**


Cette section fournit des conseils et divers ressources qui sont spécifiques à RevoScaleR et d’autres options dans Microsoft R.



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-r-package-management-for-sql-serverrr-package-management-for-sql-server-r-servicesmd"></a>7. &nbsp;[Gestion des packages R pour SQL Server](r/r-package-management-for-sql-server-r-services.md)

*Mise à jour : 2017-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_6) | [suivant](#TitleNum_8))

<!-- Source markdown line 22.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2add5a7e1aef02487ac875e353c51161658050a4 5da92dd8b5402266a837172bda9aaabed3162ce8  (PR=2939  ,  Filename=r-package-management-for-sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



Cette rubrique décrit les fonctionnalités de gestion de package que vous pouvez utiliser pour gérer les packages R qui sont exécutent sur une instance de SQL Server.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

**Gestion des packages à l’aide de T-SQL**


Vous pouvez continuer à installer des packages R en tant qu’administrateur sur l’ordinateur, si vous disposez des privilèges, et si vous êtes la seule personne à l’aide du serveur pour les tâches d’apprentissage machine.

Toutefois, si vous avez besoin de partager les packages avec d’autres personnes, ou si avez besoin de plusieurs personnes exécuter les tâches de machine learning sur le serveur, il est plus efficace de définir une bibliothèque de package partagé. SQL Server CE prend en charge par le biais des rôles de base de données.

L’administrateur de base de données est responsable de la configuration des rôles et l’ajout d’utilisateurs aux rôles. Via des rôles, l’administrateur de base de données peut contrôler qui a l’autorisation d’ajouter ou supprimer des packages R dans l’environnement SQL Server et que vous pouvez auditer l’installation du package.

**Rôles de base de données pour la gestion des packages**


Les nouveaux rôles de base de données suivantes prennent en charge l’installation en toute sécurité et gestion des packages R dans SQL Server :

- `rpkgs-users`: Permet aux utilisateurs d’utiliser tous les packages partagés qui ont été installées par les membres de le `rpkgs-shared` rôle.

- `rpkgs-private`: Fournit l’accès aux packages partagés avec les mêmes autorisations que le `rpkgs-users` rôle. Les membres de ce rôle peuvent également installer, supprimer et utiliser des packages à étendue privée.

-  `rpkgs-shared`: Fournit les mêmes autorisations que le `rpkgs-private` rôle. Les utilisateurs membres de ce rôle peuvent également installer ou supprimer des packages partagés.

- `db_owner`: A les mêmes autorisations que le `rpkgs-shared` rôle. Peut également accorder aux utilisateurs le droit d’installer ou de supprimer des packages partagés et privés.

**Création d’une bibliothèque de lot externe à l’aide de T-SQL**


En outre, SQL Server 2017 prend en charge l’instruction T-SQL, **créer une bibliothèque externe**pour prendre en charge la gestion par l’administrateur de base de données de bibliothèques externes. Actuellement, vous pouvez utiliser cette instruction pour créer des bibliothèques Windows pour R. plus prise en charge est prévue dans l’avenir pour les packages de Python et pour les paquets écrits pour l’exécution sur d’autres plateformes, tels que Linux.



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-set-up-sql-server-machine-learning-services-in-databaserset-up-sql-server-r-services-in-databasemd"></a>8. &nbsp;[Configurer SQL Server Machine Learning Services (de-de base de données)](r/set-up-sql-server-r-services-in-database.md)

*Mise à jour : 2017-09-07* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_7) | [suivant](#TitleNum_9))

<!-- Source markdown line 240.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 452dc36b4d0097f9562642238ba49eea0373d25b 4d355f6494b417dd90dce3943e7176eaece7336e  (PR=3070  ,  Filename=set-up-sql-server-r-services-in-database.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=0b832a9306244210e693bde7c476269455e9b6d8) -->



Si vous créez une solution R sur un ordinateur client de science des données et que vous avez besoin exécuter du code à l’aide de l’ordinateur SQL Server en tant que le contexte de calcul, vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée.

* Pour une connexion SQL : vérifiez que la connexion a les autorisations appropriées sur la base de données dans laquelle vous allez lire des données. Vous pouvez le faire en ajoutant *se connecter à* et *sélectionnez* autorisations, ou en ajoutant de la connexion à la *db_datareader* rôle. Pour les connexions que vous avez besoin pour créer des objets, ajoutez *DDL_admin* droits. Pour les connexions qui doivent enregistrer les données dans les tables, ajoutez la connexion à la *db_datawriter* rôle.

* Pour l’authentification Windows : vous devrez peut-être configurer une source de données ODBC sur le client de science des données qui spécifie le nom d’instance et d’autres informations de connexion. Pour plus d’informations, consultez [administrateur de sources de données ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

**Étapes suivantes**


Après avoir vérifié que la fonctionnalité de l’exécution du script fonctionne dans SQL Server, vous pouvez exécuter des commandes R et Python à partir de SQL Server Management Studio, Visual Studio Code ou tout autre client qui peut envoyer des instructions T-SQL sur le serveur.

Toutefois, vous souhaiterez peut-être apporter des modifications à la configuration du système pour prendre en charge une utilisation intensive de l’apprentissage, ou ajouter de nouveaux packages R.

Cette section répertorie certaines modifications courantes que vous pouvez apporter à prendre en charge d’apprentissage.

**Ajoutez d’autres comptes de travail**


Si vous pensez que vous pouvez utiliser R importante, ou si vous prévoyez de nombreux utilisateurs d’être en cours d’exécution des scripts en même temps, vous pouvez augmenter le nombre de comptes de travail qui sont affectés au service Launchpad. Pour plus d’informations, consultez [modifier le pool de comptes d’utilisateur pour SQL Server R Services--modify-the-user-account-pool-for-sql-server-r-services.md).

**<a name="bkmk_optimize"></a>Optimiser le serveur pour l’exécution du script externe**




&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-sql-server-configuration-for-use-with-rrsql-server-configuration-r-servicesmd"></a>9. &nbsp;[Configuration de SQL Server pour une utilisation avec R](r/sql-server-configuration-r-services.md)

*Mise à jour : 2017-07-27* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_8) | [suivant](#TitleNum_10))

<!-- Source markdown line 149.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3f57bae70e3c118c1e2bcd57017322940bae83f8 f296242d470db47077cba4215ef420bd0c60bf33  (PR=2660  ,  Filename=sql-server-configuration-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=70a1fd4dbec68d22187585de69a1d603c39e259e) -->



Si la requête retourne un seul nœud mémoire (nœud 0), vous ne disposez pas de matériel NUMA, soit le matériel est configuré comme entrelacé (non-NUMA). SQL Server ignore également les matériels NUMA lorsqu’il n’y des quatre ou moins de processeurs, ou si au moins un nœud n’a qu’un seul processeur.

Si votre ordinateur dispose de plusieurs processeurs, mais n’a pas de matériel NUMA, vous pouvez également utiliser [Soft-NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) de subdiviser les processeurs en groupes plus petits.  Dans SQL Server 2016 et SQL Server 2017, la fonctionnalité Soft-NUMA est automatiquement activée lors du démarrage du service SQL Server.

Lorsque Soft-NUMA est activée, SQL Server gère automatiquement les nœuds ; Toutefois, pour optimiser les charges de travail spécifiques, vous pouvez désactiver _affinité logicielle_ et configurer manuellement l’affinité du processeur pour les nœuds NUMA logicielles. Cela peut vous donner plus de contrôle sur lequel les charges de travail sont attribués à quels nœuds, en particulier si vous utilisez une édition de SQL Server qui prend en charge la gouvernance des ressources. En spécifiant l’affinité du processeur et alignement des pools de ressources avec des groupes de processeurs, vous pouvez réduire la latence et assurez-vous que les processus connexes sont exécutées dans le même nœud NUMA.

Le processus global de la configuration soft-NUMA et l’affinité du processeur pour prendre en charge les charges de travail R est la suivante :

1. Permettre soft-NUMA, si disponible
2. Définir l’affinité du processeur
3. Créer des pools de ressources pour les processus externes, à l’aide de [Resource Governor--... /r/Resource-Governance-for-r-services.MD)
4. Affecter les [groupes de charges de travail--... /.. / relational-databases/resource-governor/resource-governor-workload-group.md) à des groupes d’affinités spécifiques

Pour plus d’informations, y compris les exemples de code, consultez ce didacticiel : [optimisation conseils et astuces SQL (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**Autres ressources :**



&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-performance-tuning-for-r-in-sql-serverrsql-server-r-services-performance-tuningmd"></a>10. &nbsp;[Réglage des performances pour R dans SQL Server](r/sql-server-r-services-performance-tuning.md)

*Mise à jour : 2017-07-19* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_9) | [suivant](#TitleNum_11))

<!-- Source markdown line 76.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9c30753efdec81e499d5654b5b7a07f0cfe5b003 136a9f483bc8c9e1f69cf9d340d1472c21a52ec4  (PR=2565  ,  Filename=sql-server-r-services-performance-tuning.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=cf8509cab2424529ca0ed16c936fa63a139dfca4) -->



- Configurer l’instance de SQL Server pour équilibrer les opérations de moteur de base de données et de R ou Python script d’exécution aux niveaux appropriés. Cela peut inclure la modification des valeurs par défaut de SQL Server pour la mémoire et l’utilisation du processeur, NUMA et les paramètres d’affinité du processeur et la création de groupes de ressources.

- Optimiser l’ordinateur du serveur pour prendre en charge l’utilisation efficace de scripts externes. Cela peut inclure l’augmentation du nombre de comptes utilisés pour l’exécution du script externe, l’activation de gestion des packages, et affectation d’utilisateurs à liées à des rôles de sécurité.

- Application optimisations spécifiques au stockage de données et de transfert dans SQL Server, y compris l’indexation et les stratégies de statistiques, création de requête et l’optimisation des requêtes et la structure des tables qui sont utilisés pour l’apprentissage. Vous pouvez également analyser les sources de données et données modes de transport, ou modifier les processus ETL pour optimiser l’extraction de la fonctionnalité.

- Paramétrer le modèle analytique pour éviter le manque d’efficacité. L’étendue des optimisations possibles dépendent de la complexité de votre code R et les packages et les données que vous utilisez. Tâches clés incluent en éliminant les transformations de données onéreuse ou déchargeant des données de préparation ou de fonctionnalité ingénieries tâches de R ou Python pour les processus ETL ou SQL. Vous pourrez également refactoriser les scripts, éliminer en ligne package installe, divisez le code R dans des procédures distinctes pour l’apprentissage, de calcul de score et d’évaluation ou simplifier le code de travailler plus efficacement comme une procédure stockée.

**Articles de cette série**


+ [Réglage des performances pour R dans SQL Server - matériel--... \r\sql-Server-Configuration-r-services.MD)

    Fournit des conseils pour la configuration du matériel qui.. ! NCLURE-NotShown--ssNoVersion_md--... \..\includes\ssnoversion-md.md)] est installé et pour la configuration de l’instance de SQL Server pour mieux prendre en charge de scripts externes. Il est particulièrement utile pour **les administrateurs de base de données**.

+ [Réglage des performances pour R dans SQL Server - optimisation du code et les données--... \r\r-and-Data-Optimization-r-services.MD)



&nbsp;

&nbsp;

---

<a name="TitleNum_11"/>

### <a name="11-nbsp-data-science-scenarios-and-solution-templatestutorialsdata-science-scenarios-and-solution-templatesmd"></a>11. &nbsp;[Des scénarios de science des données et des modèles de solution](tutorials/data-science-scenarios-and-solution-templates.md)

*Mise à jour : 2017-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_10) | [suivant](#TitleNum_12))

<!-- Source markdown line 45.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 22c621731015f2192cb0b8d61b22062a4be50e70 6cf9e3f0a3803ed2bce9c4ffadfd7314f15f6b51  (PR=2964  ,  Filename=data-science-scenarios-and-solution-templates.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=7b4f037616e0559ac62bbae5dbe04aeffe529b06) -->



[Prévoir comment et quand contacter les prospects](https://microsoft.github.io/r-server-campaign-optimization/)

**Ce que :** cette solution utilise des données du secteur des assurances pour prédire les prospects selon les données démographiques, les données de réponse d’historique et les détails spécifiques au produit.  Recommandations sont également générées pour indiquer le canal meilleures et le temps aux utilisateurs d’approche pour influencer le comportement d’achat.

**Comment :** la solution crée et compare plusieurs modèles. La solution montre également l’intégration de données automatisés et la préparation des données à l’aide de procédures stockées. Exemples parallèles sont fournis pour SQL Server dans-base de données dans Azure et HDInsight Spark.

**Soins de santé : prévoir la durée de hôpital**


[Prédiction de durée de nombre](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**Ce que :** prévision précise les patients peuvent nécessiter hospitalisation à long terme est une partie importante de soins et de planification. Les administrateurs doivent être en mesure de déterminer les installations nécessitent plus de ressources et personnel de santé souhaitez garantir qu’ils peuvent répondre aux besoins de patients.

**Procédure :** cette solution utilise l’ordinateur virtuel de science des données et inclut une instance de SQL Server avec machine learning est activé. Il inclut également un ensemble de rapports Power BI que vous pouvez utiliser pour interagir avec un modèle déployé.

**Évolution du code client**


[Modèle de prévision de l’évolution du client (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/Introduction.md)

**Ce que :** analyse et prédiction d’évolution du code client est important dans n’importe quel secteur d’activité où la perte de clients à des concurrents doit être gérée et a empêché : bancaire, télécommunications et vente au détail, à titre d’exemple. L’objectif de l’analyse de l’attrition consiste à identifier les clients susceptibles de passer à la concurrence, puis d’effectuer les actions appropriées pour conserver ces clients.



&nbsp;

&nbsp;

---

<a name="TitleNum_12"/>

### <a name="12-nbsp-whats-new-in-machine-learning-services-in-sql-serverwhat-s-new-in-sql-server-machine-learning-servicesmd"></a>12. &nbsp;[Quelles sont les nouveautés dans Machine Learning Services dans SQL Server](what-s-new-in-sql-server-machine-learning-services.md)

*Mise à jour : 2017-08-02* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_11))

<!-- Source markdown line 33.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 025e68a93895a3788a63847cd91bff068775acf3 6dc0be2920c670235038a126d135e08d6f16ec3a  (PR=2712  ,  Filename=what-s-new-in-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=ea75391663eb4d509c10fb785fcf321558ff0b6e) -->



> Services de formation d’ordinateur, y compris l’utilisation de R ou Python, ne sont actuellement pas pris en charge lors de l’exécution de SQL Server sur Linux, ou dans la base de données SQL Azure. Recherchez les modifications apportées à une version ultérieure.
>
> Toutefois, calculer les scores natif à l’aide de la fonction PREDICT sont actuellement pris en charge dans l’édition de Linux.

**Intégration de Python dans base de données**


Vous pouvez exécuter les Python dans les procédures stockées, ou exécutez Python à distance à l’aide de l’ordinateur SQL Server en tant que le contexte de calcul. Cette intégration ouvre de nouvelles voies de grande Communauté de Python aux développeurs et les données des chercheurs exploiter la puissance de SQL Server et pour explorer des innovations de Microsoft tels que **revoscalepy** et **microsoftml**.

Les développeurs SQL Server pour accéder à des bibliothèques de Python complètes à partir de l’écosystème open source, y compris les infrastructures plébiscitées telles que scikit-en savoir plus, Tensorflow, Caffe et Theano/Keras.

Mais en cours d’exécution Python dans base de données n’est pas simplement pour l’apprentissage ; Il existe une multitude d’autres applications potentielles pour l’intégration de Python avec SQL, en exploitant les avantages offerts par les langages respectifs pour offrir des solutions puissantes plus intelligentes.

+ **revoscalepy**

    Cette version inclut la version finale de **revoscalepy**, qui fournit des équivalents Pythonic évolutives, algorithmes de RevoScaleR de diffusion en continu. Vous pouvez créer des modèles de Python pour des régressions linéaires et logistiques, les arbres de décision, les arbres augmentés et les forêts aléatoires, tout parallèles et capables de les exécuter dans des contextes de calcul à distance.

    Pour plus d’informations, consultez [What ' revoscalepy--python/what-est-revoscalepy.md).

+ Contextes de calcul à distance pour Python

    Cette version prend en charge l’utilisation de plusieurs sources de données et les contextes de calcul à distance. Le chercheur de données ou le développeur peut exécuter du code Python sur un serveur SQL distant, pour Explorer les données ou de créer des modèles sans déplacement de données. L’utilisation de contextes de calcul à distance nécessite **revoscalepy**.







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Cette section répertorie les articles très similaires pour les articles récemment mis à jour dans les autres domaines au sein de notre référentiel GitHub.com public : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveau + mis à jour (3 + 12) : **avancées d’Analytique pour SQL** documents](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveau + mis à jour (5 + 0) : **se connecter à SQL** documents](../connect/new-updated-connect.md)
- [Nouveau + mis à jour (5 + 1) : **moteur de base de données pour SQL** documents](../database-engine/new-updated-database-engine.md)
- [Nouveau + mis à jour (19 + 82) : **Integration Services pour SQL** documents](../integration-services/new-updated-integration-services.md)
- [Nouveau + mis à jour (1 + 8) : **Linux pour SQL** documents](../linux/new-updated-linux.md)
- [Nouveau + mis à jour (12 + 1) : **des bases de données relationnelles pour SQL** documents](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + mis à jour (0 + 1) : **Reporting Services pour SQL** documents](../reporting-services/new-updated-reporting-services.md)
- [Nouveau + mis à jour (7 + 1) : **Microsoft SQL Server** documents](../sql-server/new-updated-sql-server.md)
- [Nouveau + mis à jour (1 + 1) : **SQL Server Data Tools (SSDT)** documents](../ssdt/new-updated-ssdt.md)
- [Nouveau + mis à jour (0 + 2) : **SQL Server Migration Assistant (SSMA)** documents](../ssma/new-updated-ssma.md)
- [Nouveau + mis à jour (1 + 4) : **SQL Server Management Studio (SSMS)** documents](../ssms/new-updated-ssms.md)
- [Nouveau + mis à jour (4 + 1) : **Transact-SQL** documents](../t-sql/new-updated-t-sql.md)
- [Nouveau + mis à jour (0 + 1) : **Tools pour SQL** documents](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveau + mis à jour (0 0 +) : **Analysis Services pour SQL** documents](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveau + mis à jour (0 0 +) : **Master Data Services (MDS) pour SQL** documents](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)



