---
title: Setserviceaccountpassword, méthode (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccountPassword Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccountPassword method
ms.assetid: e577a1ac-985c-4799-bb38-9393efc3def2
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 113d84526b34f9f702cd8da68a06c055c3b559e3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63062327"
---
# <a name="setserviceaccountpassword-method-sqlservice-class"></a>Méthode SetServiceAccountPassword (classe SqlService)
  Modifie le mot de passe pour le compte sous lequel le service référencé s'exécute.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetServiceAccountPassword(  
AccountOldPassword , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](sqlservice-class.md) qui représente le service.  
  
#### <a name="parameters"></a>Paramètres  
 *AccountOldPassword*  
 Valeur de chaîne qui spécifie le mot de passe existant pour le compte.  
  
 *ServiceStartPassword*  
 Valeur de chaîne qui spécifie le nouveau mot de passe pour le compte.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32`, égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
