---
title: volet SQL
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], SQL pane
- View Designer, SQL pane
- SQL pane [Visual Database Tools]
ms.assetid: dbabab18-0614-415b-a2ef-9bcd0d320d5c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 5b9136e9f24447f57bc375a8ff9d8ec83ef17bd9
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008194"
---
# <a name="sql-pane-visual-database-tools"></a>Volet SQL (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Vous pouvez utiliser le volet SQL pour créer votre propre instruction SQL, ou utiliser le volet Critères et le volet Schéma pour créer l'instruction, auquel cas les instructions SQL sont créées dans le volet SQL. Pendant la génération de la requête, le volet SQL se met automatiquement à jour et se reformate pour une lecture plus aisée.  
  
Pour ouvrir le volet SQL, ouvrez d’abord le Concepteur de requêtes et de vues (quand un objet de base de données est sélectionné dans l’Explorateur de serveurs, cliquez sur **Nouvelle requête** dans le menu **Base de données**). Ensuite, dans le menu **Concepteur de requêtes** , pointez sur **Volet** et cliquez sur **SQL**.  
  
Dans le volet SQL, vous pouvez :  
  
-   entrer des instructions SQL pour créer des requêtes ;  
  
-   modifier l'instruction SQL créée par le Concepteur de requêtes et de vues sur la base des paramètres spécifiés dans les volets Schéma et Critères ;  
  
-   entrer des instructions tirant parti de fonctionnalités spécifiques de la base de données que vous utilisez.  
  
> [!NOTE]  
> Vous devez connaître les règles d'identification des objets de la base de données que vous utilisez. Pour plus d'informations, consultez la documentation du système de gestion de votre base de données.  
  
## <a name="statements-in-the-sql-pane"></a>Instructions dans le volet SQL  
Il est possible de modifier la requête en cours directement dans le volet SQL. Si vous allez dans un autre volet, le Concepteur de requêtes et de vues formate automatiquement l'instruction, puis modifie les volets Schéma et Critères en conséquence.  
  
Si votre instruction ne peut pas être représentée dans les volets Schéma et Critères alors que ces derniers sont visibles, le Concepteur de requêtes et de vues affiche une erreur et vous propose de choisir entre deux actions :  
  
-   ignorer le fait que l'instruction ne peut pas être représentée dans les volets Schéma et Critères ;  
  
-   annuler la modification qui ne peut pas être représentée et revenir à la version précédente de l'instruction SQL.  
  
Si vous choisissez d'ignorer le fait que l'instruction ne peut pas être représentée dans les volets Schéma et Critères, le Concepteur de requêtes et de vues estompe les autres volets pour indiquer qu'ils ne reflètent plus le contenu du volet SQL.  
  
Vous pouvez continuer à modifier l'instruction et à l'exécuter, comme vous le feriez avec n'importe quelle instruction SQL.  
  
> [!NOTE]  
> Si vous entrez une instruction SQL, puis apportez d'autres modifications à la requête dans les volets Schéma et Critères, le Concepteur de requêtes et de vues régénère et réaffiche l'instruction SQL. Dans certains cas, l'instruction SQL obtenue a une construction différente de celle que vous aviez entrée à l'origine (mais elle donne toujours les mêmes résultats). Vous constaterez très vraisemblablement cette différence si vous utilisez des conditions de recherche impliquant plusieurs clauses liées par AND et OR.  
  
## <a name="see-also"></a>Voir aussi  
[Créer des requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-queries-visual-database-tools.md)  
[Exécuter des requêtes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/run-queries-visual-database-tools.md)  
[Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Volet Diagramme &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)  
[Volet Critères &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)  
[Volet Résultats &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)  
  
