---
description: Méthode SetDisable (classe ServerNetworkProtocolIPAddress)
title: Méthode SetDisable (ServerNetworkProtocolIPAddress)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDisable Method (ServerNetworkProtocolIPAddress Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDisable method
ms.assetid: 7a7cc8cc-9fb8-4bf5-b483-2150d633ee10
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2ce3332f08e8044ed6e4797eb144043de8f82e6c
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516945"
---
# <a name="setdisable-method-servernetworkprotocolipaddress-class"></a>Méthode SetDisable (classe ServerNetworkProtocolIPAddress)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Désactive l'adresse IP.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetDisable()  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe ServerNetworkProtocolIPAdress](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) qui représente une adresse IP pour le protocole réseau sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
