---
description: Curseurs statiques dans ODBC
title: Curseurs statiques ODBC | Microsoft Docs
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
ms.openlocfilehash: 9689badd39e21f82c268be904b29ffb1fa90a8ae
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429161"
---
# <a name="odbc-static-cursors"></a>Curseurs statiques dans ODBC
Un curseur statique est un curseur dans lequel le jeu de résultats semble être statique. En général, il ne détecte pas les modifications apportées à l’appartenance, à l’ordre ou aux valeurs du jeu de résultats après l’ouverture du curseur. Par exemple, supposons qu’un curseur statique extrait une ligne et qu’une autre application met à jour cette ligne. Si le curseur statique réextrait la ligne, les valeurs qu’elle voit sont inchangées, en dépit des modifications apportées par l’autre application.  
  
 Les curseurs statiques peuvent détecter leurs propres mises à jour, suppressions et insertions, même si ce n’est pas obligatoire. Le fait qu’un curseur statique particulier détecte ces modifications est signalé par l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**. Les curseurs statiques ne détectent jamais d’autres mises à jour, suppressions et insertions.  
  
 Le tableau d’état de ligne spécifié par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR peut contenir SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO ou SQL_ROW_ERROR pour n’importe quelle ligne. Elle retourne SQL_ROW_UPDATED, SQL_ROW_DELETED ou SQL_ROW_ADDED pour les lignes mises à jour, supprimées ou insérées par le curseur, en supposant que le curseur peut détecter ces modifications.  
  
 Les curseurs statiques sont généralement implémentés en verrouillant les lignes dans le jeu de résultats ou en créant une copie, ou instantané, du jeu de résultats. Bien que le verrouillage des lignes soit relativement facile à faire, il présente l’inconvénient de réduire la concurrence de manière significative. La création d’une copie permet une plus grande concurrence et permet au curseur d’effectuer le suivi de ses propres mises à jour, suppressions et insertions en modifiant la copie. Toutefois, une copie est plus coûteuse à créer et peut s’écarter des données sous-jacentes, car ces données sont modifiées par d’autres.
