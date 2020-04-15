---
title: Récupération des signets (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d146b2fb9bfc0e7294709e971f1b6752dc99ab3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300069"
---
# <a name="retrieving-bookmarks"></a>Récupération des signets
Si l’application utilise des signets, elle doit définir l’attribut SQL_ATTR_USE_BOOKMARKS déclaration à SQL_UB_VARIABLE avant de préparer ou d’exécuter la déclaration. Ceci est nécessaire parce que la construction et l’entretien des signets peuvent être une opération coûteuse, de sorte que les signets ne doivent être activés que lorsqu’une application peut en faire bon usage.  
  
 Les signets sont retournés comme colonne 0 de l’ensemble de résultat. Il y a trois façons pour une application de les récupérer :  
  
-   Bind colonne 0 de l’ensemble de résultat. **SQLFetch** ou **SQLFetchScroll** renvoie les signets pour chaque rangée dans le rame ainsi que les données pour d’autres colonnes liées.  
  
-   Appelez **SQLSetPos** pour positionner à une rangée dans le ramage, puis appelez **SQLGetData** pour la colonne 0. Si un conducteur prend en charge les signets, il doit toujours prendre en charge la possibilité d’appeler **SQLGetData** pour la colonne 0, même s’il ne permet pas aux applications d’appeler **SQLGetData** pour d’autres colonnes avant la dernière colonne liée.  
  
-   Appelez **SQLBulkOperations** avec *l’argument de l’opération* mis à SQL_ADD, et la colonne 0 lié. Le curseur insère la ligne et renvoie le signet de la rangée dans le tampon lié.
