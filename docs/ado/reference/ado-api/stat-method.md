---
description: Stat, méthode
title: STAT, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
author: rothja
ms.author: jroth
ms.openlocfilehash: e4a79dc76537bbcbabc8b8689638ff9c670413e3
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777358"
---
# <a name="stat-method"></a>Stat, méthode
Récupère des informations sur un objet de [flux](./stream-object-ado.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur de **type long** indiquant l’état de l’opération.  
  
#### <a name="parameters"></a>Paramètres  
 *StatStg*  
 Une structure STATSTG qui est remplie avec des informations sur le flux. L’implémentation de la méthode **Stat** utilisée par l’objet ADO Stream ne remplit pas tous les champs de la structure.  
  
 *StatFlag*  
 Spécifie que cette méthode ne retourne pas certains membres de la structure STATSTG, ce qui entraîne l’enregistrement d’une opération d’allocation de mémoire. Les valeurs sont extraites de l’énumération STATFLAG. L’énumération STATFLAG a deux valeurs  
  
|Constant|Valeur|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1|  
  
## <a name="remarks"></a>Notes  
 La version de la méthode stat implémentée pour l’objet ADO Stream remplit les champs suivants de la structure STATSTG :  
  
 *pwcsName*  
 Chaîne contenant le nom du flux, s’il en existe un et que la valeur StatFlag STATFLAG_NONAME n’a pas été spécifiée.  
  
 *cbSize*  
 Spécifie la taille en octets du flux ou du tableau d'octets.  
  
 *mtime*  
 Indique l'heure de la dernière modification de ce stockage, flux ou tableau d'octets.  
  
 *ctime*  
 Indique l'heure de création de ce stockage, flux ou tableau d'octets.  
  
 *atime*  
 Indique l’heure du dernier accès à ce stockage, flux ou tableau d’octets.  
  
 Si STATFLAG_NONAME est spécifié dans le paramètre StatFlag, le nom du flux n’est pas retourné.  
  
 Si STATFLAG_NONAME n’a pas été spécifié dans le paramètre StatFlag et qu’aucun nom n’est disponible pour le flux actuel, cette valeur sera E_NOTIMPL.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](./stream-object-ado.md)