---
title: Stat, méthode | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0538a3afae1e4c0bf4159d8ef6a42872f21ff6ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916871"
---
# <a name="stat-method"></a>Stat, méthode
Récupère des informations sur un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Un **Long** valeur indiquant l’état de l’opération.  
  
#### <a name="parameters"></a>Paramètres  
 *StatStg*  
 Structure STATSTG qui est remplie avec les informations relatives au flux. L’implémentation de la **Stat** méthode utilisée par l’objet ADO Stream ne renseigne pas tous les champs de la structure.  
  
 *StatFlag*  
 Spécifie que cette méthode ne retourne pas certains des membres dans la structure STATSTG, ce qui évite une opération d’allocation de mémoire. Les valeurs sont extraites à partir de l’énumération STATFLAG. L’énumération STATFLAG a deux valeurs  
  
|Constante|Value|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1|  
  
## <a name="remarks"></a>Notes  
 La version de la méthode Stat implémentée pour l’objet ADO Stream renseigne les champs de la structure STATSTG suivants :  
  
 *pwcsName*  
 Une chaîne contenant le nom du flux, si celle-ci est disponible et la valeur StatFlag STATFLAG_NONAME n’était pas spécifiée.  
  
 *cbSize*  
 Spécifie la taille en octets du flux ou du tableau.  
  
 *mtime*  
 Indique l’heure de dernière modification de ce stockage, flux ou tableau d’octets.  
  
 *ctime*  
 Indique l’heure de création de ce stockage, flux ou tableau d’octets.  
  
 *atime*  
 Indique l’heure du dernier accès pour ce stockage, flux ou tableau d’octets.  
  
 Si STATFLAG_NONAME est spécifié dans le paramètre StatFlag, le nom du flux de données n’est pas retourné.  
  
 Si STATFLAG_NONAME n’a pas été spécifié dans le paramètre StatFlag et aucun nom n’est disponible pour le flux actuel, cette valeur sera E_NOTIMPL.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
