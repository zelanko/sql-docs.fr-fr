---
title: SET DELETED Commande (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b3302dc7eecca7135dab9dff5afa376169be0f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300879"
---
# <a name="set-deleted-command"></a>SET DELETED, commande
Précise si les enregistrements marqués pour la suppression sont traités et s’ils sont disponibles pour une utilisation dans d’autres commandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ACTIVÉ  
 (Par défaut pour le pilote; la valeur par défaut pour Visual FoxPro est OFF.) Précise que les commandes qui fonctionnent sur les dossiers (y compris les enregistrements dans les tableaux connexes) à l’aide d’une portée ignorent les enregistrements marqués pour la suppression.  
  
 OFF  
 Précise que les enregistrements marqués pour la suppression peuvent être consultés par des commandes qui fonctionnent sur des dossiers (y compris des enregistrements dans des tableaux connexes) à l’aide d’une portée.  
  
## <a name="remarks"></a>Notes  
 Les requêtes qui utilisent DELETED( ) pour tester l’état des enregistrements peuvent être optimisées à l’aide de la technologie Visual FoxPro Rushmore si le tableau est indexé sur DELETED ( ).  
  
> [!IMPORTANT]  
>  SET DELETED est ignoré si la portée par défaut de la commande est l’enregistrement actuel ou si vous incluez une portée d’un seul enregistrement. INDEX ignore toujours SET DELETED et indexe tous les enregistrements du tableau.  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, commande SQL](../../odbc/microsoft/delete-sql-command.md)
