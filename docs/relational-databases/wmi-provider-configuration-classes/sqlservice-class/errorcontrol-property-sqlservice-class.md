---
title: ErrorControl, propriété (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- ErrorControl Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cc70c05346bd246dc5a8b46ae1477eb65305f0b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751694"
---
# <a name="errorcontrol-property-sqlservice-class"></a>Propriété ErrorControl (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtient ou définit la gravité de l'erreur si le service ne peut pas démarrer au démarrage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) qui représente le service.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur de chaîne qui spécifie la gravité de l'erreur signalée si le service échoue au démarrage. Le tableau suivant répertorie les valeurs possibles.  
  
 Ignore  
 L'utilisateur n'est pas notifié.  
  
 Normale  
 L'utilisateur est notifié.  
  
 Severe  
 Le système est redémarré avec la dernière bonne configuration connue.  
  
 Critique  
 Le système tente de redémarrer avec une bonne configuration.  
  
 Unknown  
 La gravité est inconnue.  
  
## <a name="remarks"></a>Notes  
 La valeur indique l'action prise par le programme de démarrage en cas d'échec. Toutes les erreurs sont journalisées par le système informatique.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
