---
title: Propriété adressesIP (classe ServerNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
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
ms.openlocfilehash: e7b2adf53bc6ebca14e2d3b4dc2cee248a4b6720
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63190300"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a>Propriété IpAddresses (classe ServerNetworkProtocol)
  Obtient les adresses IP associées au protocole réseau serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.IpAddresses [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *dessin*  
 `ServerNetworkProtocol` Objet qui représente le protocole réseau utilisé par l’instance de. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Tableau d’objets de [classe ServerNetworkProtocolIPAdress](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) qui représentent les adresses IP prises en charge par le protocole réseau serveur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
