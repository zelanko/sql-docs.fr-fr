---
title: Créer des requêtes UNION (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1f4fb949c7706aa5b476edde388d747411f3a1a3
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699521"
---
# <a name="create-union-queries-visual-database-tools"></a>Créer des requêtes UNION (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Le mot clé UNION vous permet d'inclure les résultats de deux instructions SELECT dans une table résultante. Toutes les lignes retournées par l'une ou l'autre instruction SELECT sont mixées dans le résultat de l'expression UNION. Pour obtenir des exemples, consultez [Exemples (Transact-SQL)](https://msdn.microsoft.com/9b9caa3d-e7d0-42e1-b60b-a5572142186c).  
  
> [!NOTE]  
> Le volet Schéma ne peut afficher qu'une clause SELECT. Par conséquent, lorsque vous utilisez une requête UNION, le Concepteur de requêtes masque le volet Table Operations.  
  
### <a name="to-create-a-merged-select-query"></a>Pour créer une requête SELECT fusionnée  
  
1.  Ouvrez une requête ou créez-en une nouvelle.  
  
2.  Dans le volet SQL, tapez une expression UNION valide.  
  
    L'exemple suivant est une expression UNION valide.  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  Dans le menu **Concepteur de requêtes** , cliquez sur **Exécuter SQL** pour exécuter la requête.  
  
    Votre requête UNION est à présent mise en forme par le Concepteur de requêtes.  
  
## <a name="see-also"></a> Voir aussi  
[Types de requêtes pris en charge (Visual Database Tools)](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Rubriques de procédures relatives à la conception de requêtes et de vues (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Effectuer des opérations de base concernant les requêtes (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[UNION (Transact-SQL)](https://msdn.microsoft.com/607c296f-8a6a-49bc-975a-b8d0c0914df7)  
  
