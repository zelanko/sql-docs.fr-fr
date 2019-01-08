---
title: Setdisable, méthode (classe ServerNetworkProtocolIPAddress) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 7a7cc8cc-9fb8-4bf5-b483-2150d633ee10
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: adaa66fd04f6e3b6f97b4e4edc75d9a21ea4e31f
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358781"
---
# <a name="setdisable-method-servernetworkprotocolipaddress-class"></a>Méthode SetDisable (classe ServerNetworkProtocolIPAddress)
  Désactive l'adresse IP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Un servernetworkprotocolipaddress [classe ServerNetworkProtocolIPAdress]-class.md) objet qui représente une adresse IP pour le protocole réseau sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
