---
description: Méthode SetEnable (classe ClientNetworkProtocol)
title: Méthode SetEnable (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetEnable Method (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetEnable method
ms.assetid: a66c756a-1311-4f4a-8088-818f8ed90056
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1a4fa2a1bb7dda435676564989c1fb648eb3a956
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89521358"
---
# <a name="setenable-method-clientnetworkprotocol-class"></a>Méthode SetEnable (classe ClientNetworkProtocol)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Active le protocole réseau client spécifié par la configuration des [protocoles clients](https://technet.microsoft.com/library/ms181035.aspx).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetEnableMethod()  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 A [classe ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) qui représente le protocole réseau utilisé par le client [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** , égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau clients](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
