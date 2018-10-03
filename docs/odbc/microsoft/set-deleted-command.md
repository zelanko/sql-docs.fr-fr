---
title: SET DELETED, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET DELETED command [ODBC]
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5efbd7e98b430128e52634f5c7d71597afc89ace
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806067"
---
# <a name="set-deleted-command"></a>SET DELETED, commande
Spécifie si les enregistrements marqués pour suppression sont traités et si elles sont disponibles pour une utilisation dans d’autres commandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 (Par défaut pour le pilote ; la valeur par défaut pour Visual FoxPro est désactivée (OFF).) Spécifie que les commandes qui fonctionnent sur les enregistrements (y compris les enregistrements dans les tables associées) à l’aide d’une étendue ignorer les enregistrements marqués pour suppression.  
  
 OFF  
 Spécifie que les enregistrements marqués pour suppression peut être accessible par les commandes qui fonctionnent sur les enregistrements (y compris les enregistrements dans les tables associées) à l’aide d’une étendue.  
  
## <a name="remarks"></a>Notes  
 Interroge que () supprimé pour tester le statut des enregistrements d’utilisation peut être optimisée à l’aide de la technologie Visual FoxPro Rushmore si la table est indexée sur () supprimé.  
  
> [!IMPORTANT]  
>  SET DELETED est ignorée si l’étendue par défaut pour la commande est l’enregistrement actif ou si vous incluez une étendue d’un enregistrement unique. L’INDEX ignore SET DELETED toujours et indexe tous les enregistrements dans la table.  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, commande SQL](../../odbc/microsoft/delete-sql-command.md)
