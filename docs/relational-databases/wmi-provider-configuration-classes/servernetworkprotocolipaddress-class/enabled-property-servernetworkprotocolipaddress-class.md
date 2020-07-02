---
title: Propriété Enabled (ServerNetworkProtocolIpAddress)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Enabled Property (ServerNetworkProtocolIpAddress Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Enabled property
ms.assetid: 870fd4d0-6c77-462a-b480-d42eb044b2e7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a6a033243b552495734a9a3cc9aad69e0518d2c2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786052"
---
# <a name="enabled-property-servernetworkprotocolipaddress-class"></a>Propriété Enabled (classe ServerNetworkProtocolIpAddress)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Obtient la propriété booléenne qui spécifie si une adresse IP est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.Enabled [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 A [classe ServerNetworkProtocolIPAdress](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) qui représente une adresse IP pour le protocole réseau sur l'instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur booléenne qui spécifie si l'adresse IP est activée : **true** si l'adresse IP est activée ou **false** si l'adresse IP est désactivée.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
