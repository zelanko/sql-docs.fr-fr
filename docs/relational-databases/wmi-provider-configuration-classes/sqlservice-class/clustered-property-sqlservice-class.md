---
description: Propriété Clustered (classe SqlService)
title: Propriété Clustered (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Clustered Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- Clustered property
ms.assetid: f714e7f5-c2db-45c6-9536-6ca2cb5b42aa
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 693c2f9e55683a3d9bb680359f211ce3f72f93dd
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89550834"
---
# <a name="clustered-property-sqlservice-class"></a>Propriété Clustered (classe SqlService)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Obtient la valeur de propriété booléenne qui spécifie si le service fait partie d'une instance en cluster.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.Clustered [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Une valeur booléenne qui spécifie si le service participe à une instance en cluster : **true** si le service participe à une instance en cluster ou **false** si le service ne participe pas à une instance en cluster.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
