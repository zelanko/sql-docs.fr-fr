---
title: ExitCode, propriété (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- ExitCode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6852086b6e65857284f7c5ee37e550b11d66839f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064829"
---
# <a name="exitcode-property-sqlservice-class"></a>Propriété ExitCode (classe SqlService)
  Obtient ou définit le code d'erreur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 qui définit les problèmes rencontrés lors du démarrage et de l'arrêt du service.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.ExitCode [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32` qui spécifie le code de sortie.  
  
## <a name="remarks"></a>Notes  
 Cette propriété a la valeur ERROR_SERVICE_SPECIFIC_ERROR (1066) lorsque l'erreur est spécifique au service représenté par cette classe. Le service attribue la valeur NO_ERROR lors de d'exécution, et à nouveau lors d'une fin normale.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
