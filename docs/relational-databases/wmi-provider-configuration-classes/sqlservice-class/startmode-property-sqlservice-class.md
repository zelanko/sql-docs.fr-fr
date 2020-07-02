---
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1adda63135bc85ae2d8a84a8e8744b04144781de
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85662113"
---
# <a name="startmode-property-sqlservice-class"></a>Propriété StartMode (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
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
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
