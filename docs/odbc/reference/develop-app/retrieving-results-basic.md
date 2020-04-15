---
title: Résultats de récupération (de base) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], about result sets
- data sources [ODBC], result sets
- empty result sets [ODBC]
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f7d01bf92fcee07940e449a2fb4bbac4f0fe6ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304330"
---
# <a name="retrieving-results-basic"></a>Récupération des résultats (de base)
Un ensemble de *résultats* est un ensemble de lignes sur la source de données qui correspond à certains critères. Il s’agit d’un tableau conceptuel qui résulte d’une requête et qui est disponible pour une application sous forme tabulaire. Les relevés **SELECT,** les fonctions de catalogue et certaines procédures créent des ensembles de résultats. Dans l’exemple suivant, la première déclaration SQL crée un ensemble de résultats contenant toutes les lignes et toutes les colonnes dans la table des ordres, et la deuxième déclaration SQL crée un ensemble de résultats contenant OrderID, SalesPerson, et colonnes de statut pour les lignes dans le tableau des commandes dans lequel le statut est OPEN:  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Un ensemble de résultats peut être vide, ce qui est différent d’aucun résultat défini du tout. Par exemple, l’instruction SQL suivante crée un ensemble de résultats vide :  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Un jeu de résultat vide n’est pas différent de tout autre ensemble de résultats, sauf qu’il n’a pas de lignes. Par exemple, l’application peut récupérer des métadonnées pour l’ensemble de résultats, peut tenter d’obtenir des lignes et doit fermer le curseur sur l’ensemble de résultats.  
  
 Le processus de récupération des lignes à partir de la source de données et de les retourner à l’application est appelé *aller chercher*. Cette section explique les éléments de base de ce processus. Pour plus d’informations sur des sujets plus avancés, tels que les curseurs de bloc et défilement, voir [Block Cursors](../../../odbc/reference/develop-app/block-cursors.md) et [Cursesors défilants](../../../odbc/reference/develop-app/scrollable-cursors.md). Pour plus d’informations sur la mise à jour, la suppression et l’insertion de lignes, voir [Mise à jour de l’aperçu des données](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Un jeu de résultats a-t-il été créé ?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Métadonnées des jeux de résultats](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Liaison de colonnes](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Extraction de données](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Fermeture du curseur](../../../odbc/reference/develop-app/closing-the-cursor.md)
