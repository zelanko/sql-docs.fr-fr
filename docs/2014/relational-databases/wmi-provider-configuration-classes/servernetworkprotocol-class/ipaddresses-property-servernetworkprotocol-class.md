---
title: Ipaddresses, propriété (classe ServerNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- IpAddresses Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5d7f500d7a49205992ed0e0b2d9f19dc8022d61e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060149"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a>Propriété IpAddresses (classe ServerNetworkProtocol)
  Obtient les adresses IP associées au protocole réseau serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.IpAddresses [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Un `ServerNetworkProtocol` objet qui représente le protocole réseau utilisé par l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Un tableau de [classe ServerNetworkProtocolIPAdress](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) objets qui représentent les adresses IP prises en charge par le protocole réseau serveur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
