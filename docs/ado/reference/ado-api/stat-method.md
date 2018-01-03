---
title: "Méthode Stat | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: _Stream::Stat
helpviewer_keywords: Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31938be266101339d70b820260466263a737f88a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="stat-method"></a>Stat, méthode
Récupère des informations sur un [flux](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **Long** valeur indiquant l’état de l’opération.  
  
#### <a name="parameters"></a>Paramètres  
 *StatStg*  
 Structure STATSTG qui est remplie avec les informations relatives au flux. L’implémentation de la **Stat** méthode utilisée par l’objet Stream ADO ne remplit pas tous les champs de la structure.  
  
 *StatFlag*  
 Spécifie que cette méthode ne retourne pas certains membres dans la structure STATSTG, ce qui évite une opération d’allocation de mémoire. Les valeurs proviennent de l’énumération STATFLAG. L’énumération STATFLAG possède deux valeurs  
  
|Constante|Valeur|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME| 1|  
  
## <a name="remarks"></a>Notes   
 La version de la méthode Stat implémentée pour l’objet Stream ADO remplit les champs suivants de la structure STATSTG :  
  
 *pwcsName*  
 Une chaîne contenant le nom du flux, s’il est disponible et la valeur StatFlag STATFLAG_NONAME n’était pas spécifiée.  
  
 *cbSize*  
 Spécifie la taille en octets du flux ou octets du tableau.  
  
 *mtime et*  
 Indique l’heure de la dernière modification de ce stockage, flux ou tableau d’octets.  
  
 *CTime*  
 Indique l’heure de création de ce stockage, flux ou tableau d’octets.  
  
 *Atime*  
 Indique l’heure de dernier accès pour ce stockage, flux ou tableau d’octets.  
  
 Si STATFLAG_NONAME est spécifié dans le paramètre StatFlag, le nom du flux de données n’est pas renvoyé.  
  
 Si STATFLAG_NONAME n’a pas été spécifié dans le paramètre StatFlag et aucun nom n’est disponible pour le flux actuel, cette valeur sera E_NOTIMPL.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
