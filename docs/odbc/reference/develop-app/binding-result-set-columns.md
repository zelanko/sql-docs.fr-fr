---
title: "Définie les colonnes de résultat de la liaison | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: 4bc9c30f-83ae-4766-a746-032953c187ad
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a893c212f54717425f5414045a2076c35e3d8b3c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="binding-result-set-columns"></a>Définie les colonnes de résultat de la liaison
Les applications peuvent lier en tant que nombre des colonnes du jeu de résultats lorsqu’ils le souhaitent, y compris tout aucune colonne de liaison. Lorsqu’une ligne de données est atteinte, le pilote retourne les données pour les colonnes liées à l’application. Indique si l’application lie toutes les colonnes du jeu de résultats dépend de l’application. Par exemple, les applications qui génèrent les rapports généralement ont un format fixe ; de telles applications créer un jeu de résultats contenant toutes les colonnes utilisées dans le rapport et ensuite lient et récupèrent les données pour toutes ces colonnes. Les applications qui affichent des écrans complète des données parfois autorisent l’utilisateur de choisir les colonnes à afficher ; de telles applications créent un jeu de résultats contenant toutes les colonnes de choix, mais lier et l’utilisateur peut récupérer les données pour les colonnes choisies par l’utilisateur.  
  
 Données peuvent être récupérées à partir des colonnes indépendantes en appelant **SQLGetData**. Cela est généralement appelé pour extraire les données longues, qui souvent dépasse la longueur d’une seule mémoire tampon et doivent être récupérées dans les parties.  
  
 Les colonnes peuvent être liés à tout moment, même après que les lignes qui ont été extraites. Toutefois, nouvelles liaisons ne prennent pas effet jusqu'à la prochaine fois qu’une ligne est extraite ; ils ne sont pas appliquées aux données à partir de lignes déjà extraites.  
  
 Une variable est liée à une colonne jusqu'à ce qu’une autre variable est liée à la colonne, jusqu'à ce que la colonne est indépendant en appelant **SQLBindCol** avec un pointeur null en tant qu’adresse de la variable, jusqu'à ce que toutes les colonnes sont déliés en appelant **SQLFreeStmt** avec l’option SQL_UNBIND, ou jusqu'à ce que l’instruction est libérée. Pour cette raison, l’application doit être sûr que toutes les variables liées restent valides tant qu’ils sont liés. Pour plus d’informations, consultez [affectation et la libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Étant donné que les liaisons de colonne sont simplement des informations associées à la structure de l’instruction, peuvent être définies dans n’importe quel ordre. Ils sont également indépendantes du jeu de résultats. Par exemple, qu'une application lie les colonnes du jeu de résultats généré par l’instruction SQL suivante :  
  
```  
SELECT * FROM Orders  
```  
  
 Si l’application exécute ensuite l’instruction SQL  
  
```  
SELECT * FROM Lines  
```  
  
 sur le même descripteur d’instruction, les liaisons de colonne pour le premier jeu de résultats sont toujours en vigueur, car ce sont les liaisons stockées dans la structure de l’instruction. Dans la plupart des cas, ceci est une pratique de programmation médiocre et doit être évitée. Au lieu de cela, l’application doit appeler **SQLFreeStmt** avec l’option SQL_UNBIND pour dissocier les anciennes colonnes, puis lier d’autres.

