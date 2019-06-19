---
title: Les curseurs statiques ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ddd2b4d998ab2718757db4dd58de6aea8bee05e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62799009"
---
# <a name="odbc-static-cursors"></a>Curseurs statiques dans ODBC
Un curseur statique est un dans lequel le jeu de résultats apparaît comme statique. Généralement, il ne détecte pas les modifications qui ont été apportées à l’appartenance, l’ordre ou les valeurs du jeu de résultats après l’ouverture du curseur. Par exemple, un curseur statique extrait une ligne et une autre application, puis met à jour de cette ligne. Si le curseur statique réextrait la ligne, les valeurs sont inchangées, malgré les modifications qui ont été apportées par l’autre application.  
  
 Les curseurs statiques peuvent détecter leurs propres mises à jour, les suppressions et les insertions, bien qu’ils ne sont pas nécessaires pour cela. Indique si un curseur statique particulier détecte ces modifications est signalé via l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**. Les curseurs statiques détectent jamais autres mises à jour, suppressions et des insertions.  
  
 Le tableau d’état de ligne spécifié par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR peut contenir SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO ou SQL_ROW_ERROR pour n’importe quelle ligne. Il renvoie SQL_ROW_UPDATED, SQL_ROW_DELETED ou SQL_ROW_ADDED pour les lignes mises à jour, supprimées ou insérées par le curseur, en supposant que le curseur peut détecter ces modifications.  
  
 Les curseurs statiques sont généralement implémentées en verrouillant les lignes du jeu de résultats ou en effectuant une copie, ou d’instantané, du résultat définis. Bien que le verrouillage des lignes est relativement facile à réaliser, il présente l’inconvénient de ce qui réduit considérablement la concurrence. Effectuer une copie permet l’accès concurrentiel supérieur et permet le curseur effectuer le suivi de ses propres mises à jour, suppressions et l’insère en modifiant la copie. Toutefois, une copie est plus coûteuse à effectuer et peut différer de données sous-jacentes que ces données sont modifiées par d’autres utilisateurs.
