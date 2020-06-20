---
title: Propriété SupportAlias, (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SupportAlias Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SupportAlias property
ms.assetid: 1e7a2e87-c356-40a6-a6d9-e492467629f9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6fd06ad0921dbb113a89af77e46733a28c2226c9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061412"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>Propriété SupportAlias (classe ClientNetworkProtocol)
  Obtient la propriété booléenne qui spécifie si le protocole réseau actuel spécifié par la [méthode SetOrderValue (classe ClientNetworkProtocol)](clientnetworkprotocol-class.md) prend en charge les alias.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SupportAlias [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 A [classe ClientNetworkProtocol](clientnetworkprotocol-class.md) qui représente le protocole réseau utilisé par le client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur booléenne qui spécifie si le protocole réseau client prend en charge les alias.  
  
 Si True, le protocole réseau client prend en charge les alias.  
  
 Si False, le protocole réseau client ne prend pas en charge les alias.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [configurer des protocoles clients](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
