---
title: Protocolorder, propriété (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- ProtocolOrder Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7cda765a9a9eedb581bf8340478b97e527601147
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47717077"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>Propriété ProtocolOrder (classe ClientNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtient le numéro d'ordre du protocole réseau client actuellement référencé tel que spécifié par la [méthode SetOrderValue (classe ClientNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 A [classe ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) qui représente le protocole réseau utilisé par le client [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** qui spécifie le numéro d'ordre du protocole réseau client actuellement référencé en tant que jeu par la méthode **OrderValue** . Si le protocole réseau client est désactivé, cette valeur sera égale à zéro.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des protocoles clients](http://technet.microsoft.com/library/ms181035.aspx)   
 [Configuration des bibliothèques réseau et des protocoles réseau clients](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
