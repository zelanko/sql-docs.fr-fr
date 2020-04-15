---
title: Colonnes de l’ensemble de résultats contraignants (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 558ceb79d42d82477b70a028395de82cc023c170
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306360"
---
# <a name="binding-result-set-columns"></a>Liaison des colonnes d’un ensemble de résultats
Les applications peuvent lier autant ou aussi peu de colonnes de l’ensemble de résultat qu’ils le souhaitent, y compris la liaison aucune colonne du tout. Lorsqu’une série de données est récupérée, le pilote renvoie les données des colonnes liées à l’application. La question de savoir si l’application lie toutes les colonnes de l’ensemble de résultats dépend de l’application. Par exemple, les applications qui génèrent des rapports ont généralement un format fixe; ces applications créent un ensemble de résultats contenant toutes les colonnes utilisées dans le rapport, puis lient et récupèrent les données pour toutes ces colonnes. Les applications qui affichent des écrans pleins de données permettent parfois à l’utilisateur de décider quelles colonnes afficher; ces applications créent un ensemble de résultats contenant toutes les colonnes que l’utilisateur peut vouloir, mais lient et ne récupèrent les données que pour les colonnes choisies par l’utilisateur.  
  
 Les données peuvent être récupérées à partir de colonnes non liées en appelant **SQLGetData**. Ceci est communément appelé pour récupérer de longues données, qui dépassent souvent la longueur d’un seul tampon et doivent être récupérés en pièces.  
  
 Les colonnes peuvent être liées à tout moment, même après que les rangées ont été récupérées. Cependant, les nouvelles fixations n’entrent pas en vigueur avant la prochaine fois qu’une rangée est récupérée; ils ne sont pas appliqués aux données des rangées déjà récupérées.  
  
 Une variable reste liée à une colonne jusqu’à ce qu’une variable différente soit liée à la colonne, jusqu’à ce que la colonne ne soit pas liée en appelant **SQLBindCol** avec un pointeur nul comme adresse de la variable, jusqu’à ce que toutes les colonnes ne soient pas liées en appelant **SQLFreeStmt** avec l’option SQL_UNBIND, ou jusqu’à ce que la déclaration soit publiée. Pour cette raison, l’application doit être sûre que toutes les variables liées restent valides tant qu’elles sont liées. Pour plus d’informations, voir [Allocating and Freeing Buffers](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Étant donné que les liaisons de colonne ne sont que des informations associées à la structure de l’instruction, elles peuvent être définies dans n’importe quel ordre. Ils sont également indépendants de l’ensemble de résultats. Supposons, par exemple, qu’une application lie les colonnes de l’ensemble de résultats générés par la déclaration SQL suivante :  
  
```  
SELECT * FROM Orders  
```  
  
 Si l’application exécute alors la déclaration SQL  
  
```  
SELECT * FROM Lines  
```  
  
 sur la même poignée de relevé, les fixations de colonne pour le premier ensemble de résultat sont toujours en vigueur parce que ce sont les liaisons stockées dans la structure de l’instruction. Dans la plupart des cas, il s’agit d’une mauvaise pratique de programmation et doit être évitée. Au lieu de cela, l’application devrait appeler **SQLFreeStmt** avec la SQL_UNBIND option de délier toutes les anciennes colonnes, puis lier de nouvelles.
