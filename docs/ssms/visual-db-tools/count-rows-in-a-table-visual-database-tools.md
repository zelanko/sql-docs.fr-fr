---
description: Compter les lignes d'une table (Visual Database Tools)
title: Compter les lignes dans une table
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- totals [SQL Server], row counts
- row counts [SQL Server]
- column values [SQL Server]
- number of rows
- number of values
- counting rows
ms.assetid: dda4296a-1d16-4e77-8d6f-e295f6dd4e87
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: b4aef31efc3b7636d56d9a4cd1ba1cf07aa22830
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462859"
---
# <a name="count-rows-in-a-table-visual-database-tools"></a>Compter les lignes d'une table (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Vous pouvez compter les lignes d'une table afin de déterminer les éléments suivants :  
  
-   le nombre total de lignes dans une table, par exemple le décompte de tous les livres d'une table `titles` ;  
  
-   le nombre de lignes d'une table qui répondent à une condition spécifique, par exemple, le nombre de livres publiés par un éditeur dans une table `titles` ;  
  
-   le nombre de valeurs d'une colonne donnée.  
  
Lorsque vous comptez les valeurs d'une colonne, les valeurs null ne sont pas reprises dans le calcul. Vous pouvez, par exemple, compter le nombre de livres d'une table `titles` qui affichent des valeurs dans la colonne `advance` . Par défaut, le nombre inclut toutes les valeurs, et pas seulement les valeurs uniques.  
  
Les procédures associées aux trois types de nombres sont similaires.  
  
### <a name="to-count-all-the-rows-in-a-table"></a>Pour compter toutes les lignes d'une table  
  
1.  Assurez-vous que la table à synthétiser figure déjà dans le volet Schéma.  
  
2.  Cliquez avec le bouton droit sur un point de l’arrière-plan du volet Schéma, puis choisissez **Ajouter un groupe par** dans le menu contextuel. Le [Concepteur de requêtes et de vues](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) ajoute une colonne **Group By** à la grille dans le volet Critères.  
  
3.  Sélectionnez **&#42; (Toutes les colonnes)** dans le rectangle représentant la table ou l’objet table.  
  
    Le Concepteur de requêtes et de vues insère automatiquement le terme **Count** dans la colonne **Group By** du volet Critères et assigne un alias de colonne à la colonne que vous synthétisez. Il est possible de remplacer l'alias généré automatiquement par un autre, plus significatif. Pour plus d’informations, consultez [Créer des alias de colonnes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md).  
  
4.  Exécuter la requête  
  
### <a name="to-count-all-the-rows-that-meet-a-condition"></a>Pour compter toutes les lignes répondant à une condition  
  
1.  Assurez-vous que la table à synthétiser figure déjà dans le volet Schéma.  
  
2.  Cliquez avec le bouton droit sur un point de l’arrière-plan du volet Schéma, puis choisissez **Ajouter un groupe par** dans le menu contextuel. Le Concepteur de requêtes et de vues ajoute une colonne **Group By** à la grille dans le volet Critères.  
  
3.  Sélectionnez **&#42;(Toutes les colonnes)** dans le rectangle représentant la table ou l’objet structuré sous forme de table.  
  
    Le Concepteur de requêtes et de vues insère automatiquement le terme **Count** dans la colonne **Group By** du volet Critères et assigne un alias de colonne à la colonne que vous synthétisez. Pour créer un en-tête de colonne plus significatif dans le résultat de la requête, consultez [Créer des alias de colonnes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md).  
  
4.  Ajoutez la colonne de données sur laquelle doit porter la recherche et décochez ensuite la case dans la colonne **Sortie**.  
  
    Le Concepteur de requêtes et de vues insère automatiquement le terme **Group By** dans la colonne **Group By** de la grille.  
  
5.  Remplacez le terme **Group By** par **Where** dans la colonne **Group By**.  
  
6.  Dans la colonne **Filter** pour la colonne de données sur laquelle doit porter la recherche, entrez la condition de la recherche.  
  
7.  Exécuter la requête  
  
### <a name="to-count-the-values-in-a-column"></a>Pour compter les valeurs d'une colonne  
  
1.  Assurez-vous que la table à synthétiser figure déjà dans le volet Schéma.  
  
2.  Cliquez avec le bouton droit sur un point de l’arrière-plan du volet Schéma, puis choisissez **Ajouter un groupe par** dans le menu contextuel. Le Concepteur de requêtes et de vues ajoute une colonne **Group By** à la grille dans le volet Critères.  
  
3.  Ajoutez la colonne sur laquelle porte le comptage dans le volet Critères.  
  
    Le Concepteur de requêtes et de vues insère automatiquement le terme **Group By** dans la colonne **Group By** de la grille.  
  
4.  Remplacez le terme **Group By** par **Count** dans la colonne **Group By**.  
  
    > [!NOTE]  
    > Pour compter exclusivement des valeurs uniques, choisissez **Count Distinct**.  
  
5.  Exécuter la requête  
  
## <a name="see-also"></a>Voir aussi  
[Trier et regrouper des résultats de requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Résumer les résultats de la requête &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
  
