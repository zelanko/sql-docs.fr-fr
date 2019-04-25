---
title: Récupération des résultats (Basic) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8eb98d7c17663894e1bacdc27e431d6a54f45d3b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468660"
---
# <a name="retrieving-results-basic"></a>Récupération des résultats (de base)
Un *jeu de résultats* est un ensemble de lignes sur la source de données qui correspond à certains critères. Il est une table conceptuelle qui résulte d’une requête et qui sont disponible pour une application au format tabulaire. **Sélectionnez** instructions, fonctions de catalogue et certaines procédures créent des jeux de résultats. Dans l’exemple suivant, la première instruction SQL crée un jeu de résultats contenant toutes les lignes et toutes les colonnes dans la table Orders, et la deuxième instruction SQL crée un jeu de résultats contenant les colonnes OrderID, commercial et l’état des lignes dans la table Orders dans lequel le statut est ouvert :  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Un jeu de résultats peut être vide, ce qui diffère d’aucun jeu de résultats. Par exemple, l’instruction SQL suivante crée un jeu de résultats vide :  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Un jeu de résultats vide n’est pas différent n’importe quel autre jeu de résultats, à ceci près qu’il ne comporte aucune ligne. Par exemple, l’application peut récupérer des métadonnées pour le jeu de résultats peut tenter lignes et doit fermer le curseur sur le jeu de résultats.  
  
 Le processus de l’extraction de lignes à partir de la source de données et les retourner à l’application est appelé *l’extraction*. Cette section explique les composants de base de ce processus. Pour plus d’informations sur des sujets plus avancés, tels que les blocs et les curseurs avec défilement, consultez [curseurs de bloc](../../../odbc/reference/develop-app/block-cursors.md) et [curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md). Pour plus d’informations sur la mise à jour, suppression et insertion de lignes, consultez [la mise à jour la vue d’ensemble des données](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Un jeu de résultats a-t-il été créé ?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Métadonnées des jeux de résultats](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Liaison de colonnes](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Extraction de données](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Fermeture du curseur](../../../odbc/reference/develop-app/closing-the-cursor.md)
