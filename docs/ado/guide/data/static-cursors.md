---
title: Curseurs statiques | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 520c484bdaaa6eb59488900208993a607c5b0f7b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924117"
---
# <a name="static-cursors"></a>Curseurs statiques
Le curseur statique affiche toujours l’ensemble de résultats tel qu’il était au moment où le curseur a été ouvert pour la première fois. En fonction de l’implémentation, les curseurs statiques sont en lecture seule ou en lecture/écriture, et permettent de faire défiler vers l’avant et vers l’arrière. Le curseur statique ne détecte généralement pas les modifications apportées à l’appartenance, à l’ordre ou aux valeurs du jeu de résultats après l’ouverture du curseur. Les curseurs statiques peuvent détecter leurs propres mises à jour, suppressions et insertions, bien qu’ils ne soient pas obligés de le faire.  
  
 Les curseurs statiques ne détectent jamais d’autres mises à jour, suppressions et insertions. Par exemple, supposez qu’un curseur statique extrait une ligne et qu’une autre application met ensuite à jour cette ligne. Si l’application réextrait la ligne à partir du curseur statique, les valeurs qu’elle voit sont inchangées, malgré les modifications apportées par l’autre application. Tous les types de défilement sont pris en charge, mais les fournisseurs peuvent ou non prendre en charge les signets.  
  
 Si votre application n’a pas besoin de détecter les modifications de données et nécessite un défilement, le curseur statique est le meilleur choix. Utilisez **AdOpenStatic CursorTypeEnum** pour indiquer que vous souhaitez utiliser un curseur statique dans ADO.  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs avant uniquement](../../../ado/guide/data/forward-only-cursors.md)   
 [Curseurs de jeu de clés](../../../ado/guide/data/keyset-cursors.md)   
 [Curseurs dynamiques](../../../ado/guide/data/dynamic-cursors.md)
