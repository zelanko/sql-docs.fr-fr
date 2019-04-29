---
title: Générateur de requêtes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.querybuilder.f1
helpviewer_keywords:
- Query Builder dialog box
ms.assetid: 780752c9-6e3c-4f44-aaff-4f4d5e5a45c5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e09e41535ad878a3f20ae74df07ace7bda6fa7e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889582"
---
# <a name="query-builder"></a>Générateur de requêtes
  Utilisez la boîte de dialogue **Générateur de requêtes** pour créer une requête à utiliser dans la tâche Exécution SQL, la source OLE DB et la destination OLE DB, ainsi que la transformation de recherche.  
  
 Vous pouvez utiliser le générateur de requêtes pour réaliser les tâches suivantes :  
  
-   **Utilisation d'une représentation graphique d'une requête ou des commandes SQL** Le générateur de requêtes inclut un volet qui affiche votre requête graphiquement et un volet qui affiche le texte SQL de votre requête. Vous pouvez travailler dans le volet graphique ou dans le volet texte. Le générateur de requêtes synchronise les vues de manière à ce qu'elles soient toujours actualisées.  
  
-   **Jointure de tables associées** Si vous ajoutez plusieurs tables à votre requête, le générateur de requêtes détermine automatiquement la manière dont les tables sont associées et construit la commande de jointure appropriée.  
  
-   **Requête ou mise à jour de bases de données** Vous pouvez utiliser le générateur de requêtes pour renvoyer des données à l’aide d’instructions Transact-SQL SELECT et pour créer des requêtes qui mettent à jour, ajoutent ou suppriment des enregistrements dans une base de données.  
  
-   **Affichage et modification immédiate des résultats** Vous pouvez exécuter votre requête et travailler avec un jeu d'enregistrements dans une grille qui vous permet de faire défiler et de modifier les enregistrements de la base de données.  
  
 Les outils graphiques de la boîte de dialogue **Générateur de requêtes** permettent de créer des requêtes par glisser-déplacer. Par défaut, la boîte de dialogue Générateur de requêtes crée des requêtes SELECT, mais vous pouvez également générer des requêtes INSERT, UPDATE ou DELETE. Tous les types d'instructions SQL peuvent être analysés et exécutés dans la boîte de dialogue **Générateur de requêtes** . Pour plus d’informations sur les instructions SQL dans les packages, consultez [Requêtes Integration Services &#40;SSIS&#41;](integration-services-ssis-queries.md).  
  
 Pour en savoir plus sur le langage Transact-SQL et sa syntaxe, consultez [Référence Transact-SQL &#40;moteur de base de données&#41;](/sql/t-sql/language-reference).  
  
 Vous pouvez aussi utiliser des variables dans une requête pour fournir des valeurs à un paramètre d'entrée, pour capturer les valeurs des paramètres de sortie et pour stocker des codes de retour. Pour en savoir plus sur l’utilisation de variables dans les requêtes utilisées par les packages, consultez [Tâche d’exécution de requêtes SQL](control-flow/execute-sql-task.md), [Source OLE DB](data-flow/ole-db-source.md)et [Integration Services &#40;SSIS&#41; Queries](integration-services-ssis-queries.md). Pour en savoir plus sur l’utilisation de variables dans la tâche d’exécution de requêtes SQL, consultez [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) et [Ensembles de résultats dans la tâche d’exécution SQL](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).  
  
 Les transformations de recherche et de recherche floue peuvent aussi utiliser des variables avec des paramètres et des codes de retour. Les informations relatives à la source OLE DB s'appliquent également à ces deux transformations.  
  
## <a name="options"></a>Options  
 **Barre d'outils**  
 Utilisez la barre d'outils pour gérer les datasets, sélectionner les volets à afficher et contrôler les fonctions de requête.  
  
|Value|Description|  
|-----------|-----------------|  
|**Afficher/Masquer le volet Diagramme**|Affiche ou masque le volet **Diagramme** .|  
|**Afficher/Masquer le volet Grille**|Affiche ou masque le volet **Grille** .|  
|**Afficher/Masquer le volet SQL**|Affiche ou masque le volet **SQL** .|  
|**Afficher/Masquer le volet Résultats**|Affiche ou masque le volet **Résultats** .|  
|**Exécuter**|Exécute la requête. Les résultats s'affichent dans le volet Résultats.|  
|**Vérifier SQL**|Vérifie que l'instruction SQL est valide.|  
|**Tri croissant**|Trie dans l'ordre croissant les lignes de sortie sur la colonne sélectionnée du volet de la grille.|  
|**Tri décroissant**|Trie dans l'ordre décroissant les lignes de sortie sur la colonne sélectionnée du volet de la grille.|  
|**Supprimer le filtre**|Sélectionnez le nom d'une colonne dans le volet de la grille, puis choisissez **Supprimer le filtre** pour supprimer les critères de tri de la colonne.|  
|**Utiliser GROUP BY**|Ajoute la fonctionnalité GROUP BY à la requête.|  
|**Ajouter une table**|Ajoute une table à la requête.|  
  
 **Définition de la requête**  
 La définition de la requête fournit une barre d'outils et des volets dans lesquels définir et tester la requête.  
  
|Volet|Description|  
|----------|-----------------|  
|Volet**Diagramme** .|Affiche la requête dans un diagramme. Le diagramme illustre les tables contenues dans la requête et leur mode de jointure. Activez ou désactivez la case à cocher correspondant à une colonne de la table pour l'ajouter ou la supprimer du résultat de la requête.<br /><br /> Lorsque vous ajoutez des tables à la requête, le Générateur de requêtes crée des jointures entre les tables basées sur les tables, en fonction des clés de la table. Pour ajouter une jointure, faites glisser le champ d'une table vers un champ situé dans une autre table. Pour gérer une jointure, cliquez dessus avec le bouton droit, puis sélectionnez une option du menu.<br /><br /> Cliquez avec le bouton droit sur le volet **Diagramme** pour ajouter ou supprimer des tables, sélectionner toutes les tables et afficher ou masquer des volets.|  
|Volet**Grille** |Affiche la requête dans une grille. Vous pouvez utiliser ce volet pour ajouter et supprimer des colonnes dans la requête et modifier les paramètres de chaque colonne.|  
|Volet**SQL** |Affiche la requête sous forme de texte SQL. Les modifications effectuées dans le volet **Diagramme** et le volet **Grille** sont affichées ici et les modifications apportées ici sont affichées dans les volets **Diagramme** et **Grille** .|  
|Volet**Résultats** |Affiche les résultats de la requête lorsque vous cliquez sur **Exécuter** dans la barre d'outils.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes SQL, tâche](control-flow/execute-sql-task.md)   
 [Source OLE DB](data-flow/ole-db-source.md)   
 [Destination OLE DB](data-flow/ole-db-destination.md)   
 [Transformation de recherche](data-flow/transformations/lookup-transformation.md)   
 [Integration Services &#40;SSIS&#41; requêtes](integration-services-ssis-queries.md)   
 [MERGE dans les packages Integration Services](control-flow/merge-in-integration-services-packages.md)  
  
  
