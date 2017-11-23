---
title: Commande SET DELETED | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SET DELETED command [ODBC]
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34bcce12665dd3e0bcaa49e4c6e1ff93a807f514
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="set-deleted-command"></a>Commande SET DELETED
Spécifie si les enregistrements marqués pour suppression sont traités et si elles sont disponibles pour une utilisation dans d’autres commandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 (Par défaut pour le pilote, la valeur par défaut pour Visual FoxPro est désactivé.) Spécifie que les commandes qui fonctionnent sur les enregistrements (y compris les enregistrements dans les tables associées) à l’aide d’une étendue ignorer les enregistrements marqués pour suppression.  
  
 OFF  
 Spécifie que les enregistrements marqués pour suppression peut être accessible par les commandes qui agissent sur les enregistrements (y compris les enregistrements dans les tables associées) à l’aide d’une étendue.  
  
## <a name="remarks"></a>Notes  
 Interroge que (de DELETED) pour tester le statut des enregistrements d’utilisation peut être optimisée à l’aide de la technologie Visual FoxPro Rushmore si la table est indexée sur (de supprimés).  
  
> [!IMPORTANT]  
>  DÉFINIR supprimé est ignoré si l’étendue par défaut pour la commande est l’enregistrement actif ou si vous incluez une étendue d’un enregistrement unique. L’INDEX ignore les supprimer ensemble toujours et tous les enregistrements dans la table d’index.  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, commande SQL](../../odbc/microsoft/delete-sql-command.md)
