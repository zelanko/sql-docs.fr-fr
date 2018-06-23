---
title: Méthode SetBoolValue (classe SqlServiceAdvancedProperty) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a26fae3ba51f68dbcd2e519ea6a711b2fd471c43
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041787"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a>Méthode SetBoolValue (classe SqlServiceAdvancedProperty)
  Définit la valeur booléenne d'une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetBoolValue [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlServiceAdvancedProperty](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) qui représente une propriété avancée.  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*BoolValue*|Valeur booléenne qui spécifie la valeur de la propriété avancée.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32`, égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
 Le type de valeur de la propriété doit être booléen pour permettre l'attribution d'une valeur booléenne à la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  