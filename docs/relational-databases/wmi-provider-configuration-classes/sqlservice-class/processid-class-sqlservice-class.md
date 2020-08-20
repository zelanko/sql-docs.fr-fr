---
description: Classe ProcessId (classe SqlService)
title: ProcessId, classe (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProcessId Class (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0e998dad0b768ebfcca33b83a8128dc44c776acc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463606"
---
# <a name="processid-class-sqlservice-class"></a>Classe ProcessId (classe SqlService)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Obtient l'ID de processus système qui identifie un service de façon unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.ProcessId [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **UInt32** qui spécifie l’ID qui identifie de façon unique le processus.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a> Exemple  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
