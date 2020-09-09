---
description: Propriété ExitCode (classe SqlService)
title: Propriété ExitCode (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ExitCode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 71e5fbe4180c67560709f004ba099bb90ca83b02
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542839"
---
# <a name="exitcode-property-sqlservice-class"></a>Propriété ExitCode (classe SqlService)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Obtient ou définit le code d'erreur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 qui définit les problèmes rencontrés lors du démarrage et de l'arrêt du service.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ExitCode [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** qui spécifie le code de sortie.  
  
## <a name="remarks"></a>Notes  
 Cette propriété a la valeur ERROR_SERVICE_SPECIFIC_ERROR (1066) lorsque l'erreur est spécifique au service représenté par cette classe. Le service attribue la valeur NO_ERROR lors de d'exécution, et à nouveau lors d'une fin normale.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
