---
title: Propriété PropertyIdx (classe ClientNetworkProtocolProperty) | Documents Microsoft
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
- PropertyIdx Property (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyIdx property
ms.assetid: d7845962-ac68-4435-9c59-70ec450fec88
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 42388eb8158e12f5a4458364e39bf9ce1576e70f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043311"
---
# <a name="propertyidx-property-clientnetworkprotocolproperty-class"></a>Propriété PropertyIdx (classe ClientNetworkProtocolProperty)
  Obtient ou définit la valeur d'index de la propriété dans le tableau de propriétés référencé par la [propriété Properties (classe ClientNetworkProtocol)](../clientnetworkprotocol-class/clientnetworkprotocol-class.md) de l'objet de [classe ClientNetworkProtocol](../clientnetworkprotocol-class/clientnetworkprotocol-class.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.PropertyIdx [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 A [classe ClientNetworkProtocolProperty](clientnetworkprotocolproperty-class.md) qui représente un attribut du protocole réseau utilisé par le client [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32` qui spécifie la valeur d'index de tableau de la propriété actuelle.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des protocoles clients](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  