---
title: Multiipconfigurationsupport, propriété (classe ServerNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3a6813371e7641af1369f94f875ca0d9f96ad3a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470056"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>Propriété MultiIpConfigurationSupport (classe ServerNetworkProtocol)
  Obtient la propriété booléenne qui spécifie si plusieurs adresses IP sont prises en charge par un protocole réseau serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Un [ProtocolName, propriété (classe ServerNetworkProtocol)](servernetworkprotocol-class.md) objet qui représente le protocole réseau utilisé par l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Une valeur booléenne qui spécifie si plusieurs adresses IP sont prises en charge par le protocole réseau serveur : `true` si plusieurs adresses IP sont prises en charge par le protocole réseau serveur ou `false` si plusieurs adresses IP ne sont pas prises en charge par le protocole réseau serveur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
