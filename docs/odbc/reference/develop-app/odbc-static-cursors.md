---
title: Cursors statiques ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], static
- static cursors [ODBC]
ms.assetid: 28cb324c-e1c3-4b5c-bc3e-54df87037317
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b99566c473e88684e8b092a5ac9fc899e7dce177
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282442"
---
# <a name="odbc-static-cursors"></a>Curseurs statiques dans ODBC
Un curseur statique est celui dans lequel l’ensemble de résultat semble être statique. Il ne détecte généralement pas les modifications apportées à l’adhésion, à l’ordre ou aux valeurs du résultat fixé après l’ouverture du curseur. Par exemple, supposons qu’un curseur statique récupère une ligne et une autre application, puis met à jour cette ligne. Si le curseur statique refaçonde la ligne, les valeurs qu’il voit sont inchangées, malgré les changements qui ont été apportés par l’autre application.  
  
 Les curseurs statiques peuvent détecter leurs propres mises à jour, suppressions et inserts, bien qu’ils ne soient pas tenus de le faire. La question de savoir si un curseur statique particulier détecte ces changements est signalée par l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**. Les curseurs statiques ne détectent jamais d’autres mises à jour, suppressions et inserts.  
  
 Le tableau d’état de la ligne spécifié par l’attribut de l’instruction SQL_ATTR_ROW_STATUS_PTR peut contenir SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO ou SQL_ROW_ERROR pour n’importe quelle rangée. Il renvoie SQL_ROW_UPDATED, SQL_ROW_DELETED ou SQL_ROW_ADDED pour les lignes mises à jour, supprimées ou insérées par le curseur, en supposant que le curseur peut détecter de tels changements.  
  
 Les curseurs statiques sont généralement implémenté en verrouillant les lignes dans l’ensemble de résultat ou en faisant une copie, ou un instantané, de l’ensemble de résultat. Bien que les lignes de verrouillage soit relativement facile à faire, elle a l’inconvénient de réduire considérablement la concurrence. Faire une copie permet une plus grande concurrence et permet au curseur de garder une trace de ses propres mises à jour, supprime et insère en modifiant la copie. Cependant, une copie est plus coûteuse à faire et peut diverger des données sous-jacentes que ces données sont modifiées par d’autres.
