---
title: Properties, propriété (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Properties Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
caps.latest.revision: 33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 569c1b0f8f140bd05c2be03286e6c9fa1d66a200
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202729"
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Propriété Properties (classe ClientNetworkProtocol)
  Obtient les propriétés associées au protocole réseau client actuel spécifié par [Configurer des protocoles clients](http://technet.microsoft.com/library/ms181035.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe ClientNetworkProtocol](clientnetworkprotocol-class.md) qui représente le protocole réseau utilisé par le client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Un tableau de [classe ClientNetworkProtocolProperty](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) les objets qui représentent les propriétés prises en charge par le protocole réseau client actuel référencé par le `OrderValue` propriété.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau clients](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
