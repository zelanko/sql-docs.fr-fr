---
title: "Propriété ExitCode (classe SqlService) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ExitCode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ce081654b9e3513471e17973636b63302298cd5
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="exitcode-property-sqlservice-class"></a>Propriété ExitCode (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtient ou définit le code d'erreur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 qui définit les problèmes rencontrés lors du démarrage et de l'arrêt du service.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.ExitCode [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *objet*  
 Objet de [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** qui spécifie le code de sortie.  
  
## <a name="remarks"></a>Notes  
 Cette propriété a la valeur ERROR_SERVICE_SPECIFIC_ERROR (1066) lorsque l'erreur est spécifique au service représenté par cette classe. Le service attribue la valeur NO_ERROR lors de d'exécution, et à nouveau lors d'une fin normale.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
