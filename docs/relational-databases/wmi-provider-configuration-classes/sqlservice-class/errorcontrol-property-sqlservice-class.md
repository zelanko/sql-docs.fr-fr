---
title: ErrorControl, propriété (classe SqlService) | Microsoft Docs
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: 436c26aa6fffcfc364b47cbfbc8cf3c32e145849
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217577"
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
  
  
