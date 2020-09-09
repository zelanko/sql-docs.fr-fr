---
description: Propriété MultiIpConfigurationSupport (classe ServerNetworkProtocol)
title: Propriété MultiIpConfigurationSupport, (ServerNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9a0c29f72ab66f008dfe6ddfb87be054501aeb50
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545454"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>Propriété MultiIpConfigurationSupport (classe ServerNetworkProtocol)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Obtient la propriété booléenne qui spécifie si plusieurs adresses IP sont prises en charge par un protocole réseau serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [propriété ProtocolName (classe ServerNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/protocolname-property-servernetworkprotocol-class.md) qui représente le protocole réseau utilisé par l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur booléenne qui spécifie si plusieurs adresses IP sont prises en charge par le protocole réseau serveur : **true** si plusieurs adresses IP sont prises en charge par le protocole réseau serveur, ou **false** si plusieurs adresses IP ne sont pas prises en charge par le protocole réseau serveur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
