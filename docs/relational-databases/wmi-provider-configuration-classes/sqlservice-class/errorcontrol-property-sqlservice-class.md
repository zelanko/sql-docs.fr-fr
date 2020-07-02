---
title: ErrorControl, propriété (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
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
ms.openlocfilehash: b666426cd7f1d7eb2395ec4a67f0b166564de17d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733012"
---
# <a name="errorcontrol-property-sqlservice-class"></a>Propriété ErrorControl (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
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
  
 Ignorer  
 L'utilisateur n'est pas notifié.  
  
 Normal  
 L'utilisateur est notifié.  
  
 Severe  
 Le système est redémarré avec la dernière bonne configuration connue.  
  
 Critique  
 Le système tente de redémarrer avec une bonne configuration.  
  
 Unknown  
 La gravité est inconnue.  
  
## <a name="remarks"></a>Remarques  
 La valeur indique l'action prise par le programme de démarrage en cas d'échec. Toutes les erreurs sont journalisées par le système informatique.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
