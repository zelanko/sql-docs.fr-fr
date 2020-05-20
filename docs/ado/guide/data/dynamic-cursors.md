---
title: Curseurs dynamiques | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
author: rothja
ms.author: jroth
ms.openlocfilehash: 4a2b251e23c2408e75acd77debbc0876fd3f9c98
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761045"
---
# <a name="dynamic-cursors"></a>Curseurs dynamiques
Les curseurs dynamiques détectent toutes les modifications apportées aux lignes dans le jeu de résultats, que les modifications se produisent à l’intérieur du curseur ou par d’autres utilisateurs en dehors du curseur. Toutes les instructions INSERT, Update et Delete effectuées par tous les utilisateurs sont visibles par le biais du curseur. Le curseur dynamique peut détecter toute modification apportée aux lignes, à l’ordre et aux valeurs dans le jeu de résultats après l’ouverture du curseur. Les mises à jour effectuées en dehors du curseur ne sont pas visibles tant qu’elles ne sont pas validées (sauf si le niveau d’isolation de la transaction de curseur est défini sur « non validé »).  
  
 Par exemple, supposons qu’un curseur dynamique extrait deux lignes et une autre application, puis met à jour l’une de ces lignes et supprime l’autre. Si le curseur dynamique extrait alors ces lignes, il ne trouvera pas la ligne supprimée, mais il affichera les nouvelles valeurs pour la ligne mise à jour.  
  
 Le curseur dynamique est un bon choix si votre application doit détecter toutes les mises à jour simultanées effectuées par d’autres utilisateurs. Utilisez **AdOpenDynamic CursorTypeEnum** pour indiquer que vous souhaitez utiliser un curseur dynamique dans ADO.  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs avant uniquement](../../../ado/guide/data/forward-only-cursors.md)   
 [Curseurs statiques](../../../ado/guide/data/static-cursors.md)   
 [Curseurs de jeu de clés](../../../ado/guide/data/keyset-cursors.md)
