---
title: "Conversion de Code R pour une utilisation dans les Services de R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 0b11ab52-b2f9-4a4f-b1ab-68ba09c8adcc
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Conversion de Code R pour une utilisation dans les Services de R
Lorsque vous déplacez le code R à partir de R Studio ou un autre environnement à SQL Server, souvent le code fonctionnera sans modification supplémentaire lors de l’ajout à la *@script* paramètre de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Cela est particulièrement vrai si vous avez développé votre solution en utilisant les fonctions ScaleR, ce qui facilite la modifier les contextes d’exécution.    
    
Toutefois, en général, vous devez modifier votre code R à exécuter dans SQL Server, pour tirer parti de l’intégration plus étroite avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et pour éviter de coûteuses transferts de données.   
   
   
## Ressources  
  
Pour afficher des exemples de mode d’exécution du code R dans SQL Server, consultez ces procédures pas à pas :   
+ [Analytique base de données pour les développeurs SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)    
  Montre comment vous pouvez effectuer votre code R plus modulaire en l’intégrant à des procédures stockées  
+ [Solution de science des données de bout en bout](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)    
  Inclut une comparaison d’ingénierie dans R et T-SQL

## Modifications apportées au processus de science des données dans SQL Server  
  
Lorsque vous travaillez dans [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)], RStudio, ou autre environnement, un workflow typique consiste à extraire des données sur votre ordinateur, analyser les données de manière itérative, puis écrire ou afficher les résultats. Toutefois, lorsque le code d’autonome R est migré vers SQL Server, de ce processus peut être simplifié ou déléguée à d’autres outils de SQL Server :

| Code externe | R dans SQL Server |
|-------|-------|
| Réception des données| Définir les données d’entrée comme une requête SQL dans la base de données | 
| Résumer et visualiser des données| Aucune modification ; graphiques peuvent être exportées sous forme d’images ou envoyés à un poste de travail distant|
|Conception de fonctionnalités| Vous pouvez utiliser R dans base de données, mais il peut être plus efficace d’appeler des fonctions T-SQL ou définies par le personnalisé|
|Partie du processus d’analyse de nettoyage des données| Nettoyage des données peut être délégué à un processus ETL et effectué à l’avance|
|Prédictions de sortie dans le fichier| Prédictions de table ou encapsuler `predict` dans les procédures stockées pour un accès direct par les applications|
  

  
## Meilleures pratiques  
  
+ Prenez note des dépendances, tels que les packages requis à l’avance. Dans un environnement de test et de développement, il peut être possible d’installer des packages dans le cadre de votre code, mais il s’agit d’une mauvaise pratique dans un environnement de production. Informez l’administrateur afin que les packages peuvent être installés et testés avant le déploiement de votre code.  
+ Constituer une liste de données possibles des problèmes de type. Documentez les schémas des résultats attendus dans chaque section de code.  
+ Identifier les sources de données principales comme données de formation de modèle ou des données d’entrée pour les prévisions et sources secondaires tels que des facteurs, les variables de regroupement supplémentaire et ainsi de suite. Mappez votre plus grand jeu de données du paramètre d’entrée de [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
+ Modifier vos instructions de données d’entrée pour travailler directement dans la base de données. Plutôt que le déplacement des données vers un fichier CSV local ou rend répété appels ODBC, vous allez obtenir de meilleures performances à l’aide de requêtes SQL ou les vues qui peuvent être exécutés directement sur la base de données, en évitant le déplacement des données.  
+ Utilisez SQL Server des plans de requête pour identifier les tâches qui peuvent être effectuées en parallèle. Si la requête d’entrée peut être parallélisée, la valeur `@parallel=1` dans le cadre de vos arguments à sp_execute_external_script. Traitement avec cet indicateur parallèle est généralement possible chaque fois que SQL Server peut fonctionner avec des tables partitionnées ou distribuer une requête entre plusieurs processus et agréger les résultats à la fin. 
   Traitement avec cet indicateur en parallèle n’est généralement pas possible si vous êtes l’apprentissage des modèles à l’aide d’algorithmes qui nécessitent toutes les données à lire, ou si vous avez besoin créer des agrégats. 
+ Lorsque cela est possible, remplacez les fonctions R classiques avec **ScaleR** fonctions qui prennent en charge l’exécution distribuée. Pour plus d’informations, consultez [comparaison des fonctions dans l’échelle R et CRAN R](Summary%20of%20rx%20Functions.md).
+ Examinez votre code R afin de déterminer si des étapes qui peuvent être effectuées indépendamment, ou effectuées plus efficacement, à l’aide d’un appel de procédure stockée distincte. Par exemple, vous pouvez décider à effectuer l’extraction de l’ingénierie ou une fonctionnalité de fonctionnalité séparément et ajoutez les valeurs dans une nouvelle colonne. Utilisez T-SQL plutôt que le code R pour effectuer des calculs basés sur un jeu. Pour obtenir un exemple d’une solution R qui compare les performances de ces dernières, R pour des tâches ingénierie de fonctionnalité, consultez ce didacticiel : [procédure pas à pas au bout de science des données](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md).  
  
    
## Restrictions    
 Gardez à l’esprit les restrictions suivantes lors de la conversion de votre code R :    
   
**Types de données**    
-   Tous les types de données R sont pris en charge. Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge une plus grande variété de types de données que ne R, certaines conversions de types de données implicites sont effectuées lors de l’envoi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données R et vice versa. Vous devrez peut-être également cast ou de convertir explicitement des données.    
    
- Les valeurs NULL sont prises en charge. R utilise la `na` construire des données pour représenter des valeurs manquantes, qui est similaire aux valeurs NULL.    
    
- Pour plus d’informations, consultez la page [utilisation des Types de données R](../../advanced-analytics/r-services/working-with-r-data-types.md).    
 
 **Entrées et sorties**   
+ Vous pouvez définir qu’un seul jeu de données d’entrée dans le cadre des paramètres de procédure stockée. Cette requête d’entrée de la procédure stockée peut être une instruction SELECT unique valide. Nous vous recommandons d’utiliser cette entrée pour le jeu de données plus grand et d’obtenir des jeux de données plus petits si nécessaire en appelant RODBC. 

+ Appels précédés par EXECUTE ne peut pas servir d’une entrée de sp_execute_external_script de procédure stockée.    
    
+ Toutes les colonnes dans le jeu de données d’entrée doivent être mappés à des variables dans le script R. Les variables sont mappées automatiquement par nom. Par exemple, supposons que votre script R contient une formule comme celle-ci :    
    
    ```    
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek    
    ```    
    
     Une erreur sera déclenchée si le jeu de données d’entrée ne contient pas de colonnes avec la correspondance des noms ArrDelay, CRSDepTime, DayOfWeek, CRSDepHour et DayOfWeek.    

+ Vous pouvez également fournir plusieurs paramètres scalaires comme entrée. Toutefois, toutes les variables que vous passez comme paramètres de la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) doivent être mappés à des variables dans le code R. Par défaut, les variables sont mappées par nom.
+ Pour inclure des variables d’entrée scalaires dans la sortie du code R, ajoutez simplement le **sortie** mot clé lorsque vous définissez la variable.             
+ Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], votre code R est limité à sortir un dataset unique sous la forme d’un objet data.frame. Toutefois, vous pouvez également générer scalaires plusieurs sorties, y compris les graphiques au format binaire et de modèles au format varbinary.    
    
+ Vous pouvez généralement produire le dataset retourné par le script R sans avoir à spécifier les noms des colonnes de sortie, en utilisant l’option avec RESULT SETS UNDEFINED. Toutefois, toutes les variables du script R que vous souhaitez exporter doivent être mappés à des paramètres de sortie SQL.
    
+ Si votre script R utilise l’argument `@parallel=1`, vous devez définir le schéma de sortie. La raison est que plusieurs processus peuvent être créées par SQL Server pour exécuter la requête en parallèle, avec les résultats collectés à la fin. Par conséquent, le schéma de sortie doit être défini avant de pouvoir créer les processus parallèles.

 **Dépendances**
 + Évitez d’installer des packages à partir du code R. Sur SQL Server, les packages doivent être installés à l’avance.  
  
  
  

