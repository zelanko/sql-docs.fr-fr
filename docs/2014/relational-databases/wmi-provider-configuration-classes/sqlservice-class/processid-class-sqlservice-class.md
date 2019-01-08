---
title: Classe ProcessId (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProcessId Class (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b9e6c04a0ae0000284f3550d39e47c973adbe8ab
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53357689"
---
# <a name="processid-class-sqlservice-class"></a>Classe ProcessId (classe SqlService)
  Obtient l'ID de processus système qui identifie un service de façon unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.ProcessId [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32` qui spécifie l'ID qui identifie le processus de façon unique.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
