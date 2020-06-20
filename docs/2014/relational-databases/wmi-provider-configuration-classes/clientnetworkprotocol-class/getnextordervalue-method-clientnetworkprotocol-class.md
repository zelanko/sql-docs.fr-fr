---
title: Méthode GetNextOrderValue, (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetNextOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetNextOrderValue method
ms.assetid: d741dc5c-c225-43d9-a730-7ad664ac525f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bdc3eecd9e151d7da32a5fd65a90552c0743b3d9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062694"
---
# <a name="getnextordervalue-method-clientnetworkprotocol-class"></a>Méthode GetNextOrderValue (classe ClientNetworkProtocol)
  Sélectionne le protocole qui figure à l'emplacement suivant dans la liste de protocoles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.GetNextOrderValue()  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 A [classe ClientNetworkProtocol](clientnetworkprotocol-class.md) qui représente le protocole réseau utilisé par le client [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32`, égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des protocoles clients](https://technet.microsoft.com/library/ms181035.aspx)   
 [Configuration des bibliothèques réseau et des protocoles réseau clients](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
