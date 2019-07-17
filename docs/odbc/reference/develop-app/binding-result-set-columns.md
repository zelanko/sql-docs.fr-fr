---
title: Définie les colonnes de résultat de la liaison | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: 4bc9c30f-83ae-4766-a746-032953c187ad
author: MightyPen
ms.author: genemi
ms.openlocfilehash: becda51a0fac924fce31e6cb15331321990d8a42
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135001"
---
# <a name="binding-result-set-columns"></a>Liaison des colonnes d’un ensemble de résultats
Les applications peuvent lier en tant que colonnes autant ou aussi peu du jeu de résultats lorsqu’ils le souhaitent, y compris aucune colonne de la liaison du tout. Quand une ligne de données est récupérée, le pilote retourne les données pour les colonnes liées à l’application. Indique si l’application lie toutes les colonnes du jeu de résultats dépend de l’application. Par exemple, les applications qui génèrent les rapports généralement ont un format fixe ; de telles applications créer un jeu de résultats contenant toutes les colonnes utilisées dans le rapport et ensuite lier et récupérer les données pour l’ensemble de ces colonnes. Applications qui affichent des écrans complet de données parfois autorisent l’utilisateur de choisir les colonnes à afficher ; de telles applications créent un jeu de résultats contenant toutes les colonnes choix, mais lier et l’utilisateur peut récupérer les données pour les colonnes choisies par l’utilisateur.  
  
 Données peuvent être récupérées à partir des colonnes indépendantes en appelant **SQLGetData**. Cela est généralement appelé pour extraire les données longues, qui souvent dépasse la longueur d’une seule mémoire tampon et doivent être récupérées dans les parties.  
  
 Les colonnes peuvent être liés à tout moment, même après que les lignes qui ont été extraites. Toutefois, les nouvelles liaisons ne prennent pas effet tant que la prochaine fois qu’une ligne est extraite ; ils ne sont pas appliquées aux données à partir de lignes déjà lues.  
  
 Une variable est liée à une colonne jusqu'à ce qu’une variable différente est liée à la colonne, jusqu'à ce que la colonne est déliée en appelant **SQLBindCol** avec un pointeur null en tant qu’adresse de la variable, jusqu'à ce que toutes les colonnes sont déliés en appelant **SQLFreeStmt** avec l’option SQL_UNBIND, ou jusqu'à ce que l’instruction est libérée. Pour cette raison, l’application doit être sûr que toutes les variables liées restent valides tant qu’elles sont liées. Pour plus d’informations, consultez [allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Étant donné que les liaisons de colonne sont simplement des informations associées à la structure de l’instruction, ils peuvent être définies dans n’importe quel ordre. Ils sont également indépendantes de l’ensemble de résultats. Par exemple, qu'une application lie les colonnes du jeu de résultats généré par l’instruction SQL suivante :  
  
```  
SELECT * FROM Orders  
```  
  
 Si l’application exécute ensuite l’instruction SQL  
  
```  
SELECT * FROM Lines  
```  
  
 sur le même descripteur d’instruction, les liaisons de colonne du premier jeu de résultats sont toujours en vigueur, car ce sont les liaisons stockées dans la structure de l’instruction. Dans la plupart des cas, ceci est une pratique de programmation médiocre et doit être évitée. Au lieu de cela, l’application doit appeler **SQLFreeStmt** avec l’option SQL_UNBIND pour séparer les anciennes colonnes, puis lier d’autres.
