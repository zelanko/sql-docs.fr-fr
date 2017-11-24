---
title: "Propriété Properties (classe ClientNetworkProtocol) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Properties Property (ClientNetworkProtocol Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 33c6c8cae3f310113d5bf6d425ca41d2a75d4314
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Propriété Properties (classe ClientNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Obtient les propriétés associées avec le protocole réseau client actuel spécifié par le [configurer des protocoles clients](http://technet.microsoft.com/library/ms181035.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.Properties [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *objet*  
 Objet de [classe ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) qui représente le protocole réseau utilisé par le client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Tableau d'objets de [classe ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) qui représentent les propriétés prises en charge par le protocole réseau client actuel référencé par la propriété **OrderValue** .  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau clients](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
