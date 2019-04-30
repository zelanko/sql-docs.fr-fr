---
title: Properties, propriété (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d6c2dbfb1254260f5c92df5f1da33ba26e368aa7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192047"
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Propriété Properties (classe ClientNetworkProtocol)
  Obtient les propriétés associées au protocole réseau client actuel spécifié par [Configurer des protocoles clients](https://technet.microsoft.com/library/ms181035.aspx).  
  
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
 [Configuration des bibliothèques réseau et des protocoles réseau clients](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
