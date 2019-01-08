---
title: Setenable, méthode (classe ServerNetworkProtocolIPAddress) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: baa86deb-95dd-416f-b2c7-cec1dfb91ab4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d4c542aa1491710d49ec4c24c027e69f2eef24a9
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53349177"
---
# <a name="setenable-method-servernetworkprotocolipaddress-class"></a>Méthode SetEnable (classe ServerNetworkProtocolIPAddress)
  Active l'adresse IP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetEnable()  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 A [classe ServerNetworkProtocolIPAdress](servernetworkprotocolipaddress-class.md) qui représente une adresse IP pour le protocole réseau sur l'instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32`, égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
