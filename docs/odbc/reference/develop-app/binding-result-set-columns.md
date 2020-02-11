---
title: Colonnes de l’ensemble de résultats de liaison | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135001"
---
# <a name="binding-result-set-columns"></a>Liaison des colonnes d’un ensemble de résultats
Les applications peuvent lier autant de colonnes que vous le souhaitez dans le jeu de résultats, y compris la liaison d’aucune colonne. Lorsqu’une ligne de données est extraite, le pilote retourne les données des colonnes liées à l’application. Le fait que l’application lie toutes les colonnes du jeu de résultats dépend de l’application. Par exemple, les applications qui génèrent des rapports ont généralement un format fixe ; de telles applications créent un jeu de résultats contenant toutes les colonnes utilisées dans le rapport, puis lient et récupèrent les données pour toutes ces colonnes. Les applications qui affichent des écrans pleins de données permettent parfois à l’utilisateur de choisir les colonnes à afficher ; de telles applications créent un jeu de résultats contenant toutes les colonnes que l’utilisateur peut souhaiter, mais qui lient et récupère les données uniquement pour les colonnes choisies par l’utilisateur.  
  
 Les données peuvent être récupérées à partir de colonnes indépendantes en appelant **SQLGetData**. Cela est communément appelé pour extraire des données de type long, qui sont souvent supérieures à la longueur d’une seule mémoire tampon et doivent être extraites en parties.  
  
 Les colonnes peuvent être liées à tout moment, même après l’extraction des lignes. Toutefois, les nouvelles liaisons ne prennent pas effet avant la prochaine extraction d’une ligne. elles ne sont pas appliquées aux données des lignes déjà extraites.  
  
 Une variable reste liée à une colonne jusqu’à ce qu’une variable différente soit liée à la colonne, jusqu’à ce que la colonne soit détachée en appelant **SQLBindCol** avec un pointeur null comme adresse de la variable, jusqu’à ce que toutes les colonnes soient indépendantes en appelant **SQLFreeStmt** avec l’option SQL_UNBIND ou jusqu’à ce que l’instruction soit libérée. Pour cette raison, l’application doit s’assurer que toutes les variables liées restent valides tant qu’elles sont liées. Pour plus d’informations, consultez [allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Étant donné que les liaisons de colonnes sont simplement des informations associées à la structure d’instruction, elles peuvent être définies dans n’importe quel ordre. Elles sont également indépendantes du jeu de résultats. Supposons, par exemple, qu’une application lie les colonnes du jeu de résultats généré par l’instruction SQL suivante :  
  
```  
SELECT * FROM Orders  
```  
  
 Si l’application exécute ensuite l’instruction SQL  
  
```  
SELECT * FROM Lines  
```  
  
 sur le même descripteur d’instruction, les liaisons de colonne pour le premier jeu de résultats sont toujours en vigueur, car il s’agit des liaisons stockées dans la structure de l’instruction. Dans la plupart des cas, il s’agit d’une pratique de programmation médiocre qui devrait être évitée. Au lieu de cela, l’application doit appeler **SQLFreeStmt** avec l’option SQL_UNBIND pour dissocier toutes les anciennes colonnes, puis en lier de nouvelles.
