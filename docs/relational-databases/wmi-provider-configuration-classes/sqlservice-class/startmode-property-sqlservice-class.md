---
description: Propriété StartMode (classe SqlService)
title: StartMode, propriété (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- StartMode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f662597bf67837678690928810875f62e5d75e04
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542770"
---
# <a name="startmode-property-sqlservice-class"></a>Propriété StartMode (classe SqlService)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Obtient le mode de démarrage du service.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 qui spécifie le mode du service.  
  
 Il peut s'agir de l'une des valeurs suivantes.  
  
 Démarrage  
 Valeur = 0. Le service est démarré par le chargeur du système d'exploitation. Cette option est uniquement valide pour les services de pilote.  
  
 Système  
 Valeur = 1. Service démarré par la méthode **IoInitSystem** . Cette option est uniquement valide pour les services de pilote.  
  
 Automatique  
 Valeur = 2 Le service doit être démarré automatiquement par le Gestionnaire de contrôle des services lors du démarrage du système.  
  
 Manuel  
 Valeur = 3. Service qui doit être démarré par le gestionnaire de l’ordinateur lorsqu’un processus appelle la méthode **StartService** .  
  
 Désactivé  
 Valeur = 4 Le service ne peut pas être démarré.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
