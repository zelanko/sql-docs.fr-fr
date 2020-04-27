---
title: Propriétés de sécurité | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], properties
- SecurityPackageList property
- BuiltinAdminsAreServerAdmins property
- DisableClientImpersonation property
- ErrorMessageMode property
- RequiredProtectionLevel property
- ServiceAccountIsServerAdmin property
- RequireClientAuthentication property
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9316827245adfbcf64bd798869f570dc5f0af14c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068910"
---
# <a name="security-properties"></a>Propriétés de sécurité
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de sécurité du serveur répertoriées dans le tableau ci-dessous. Pour plus d'informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **S'applique à :** mode serveur multidimensionnel et tabulaire  
  
## <a name="properties"></a>Propriétés  
 `RequireClientAuthentication`  
 Propriété booléenne qui indique si le client doit être authentifié.  
  
 La valeur par défaut de cette propriété est True, qui indique que le client doit être authentifié.  
  
 `SecurityPackageList`  
 Propriété de type chaîne qui contient une liste (séparée par des virgules) des packages SSPI utilisés par le serveur pour l'authentification des clients.  
  
 `DisableClientImpersonation`  
 Propriété booléenne qui indique si l'emprunt d'identité du client (par exemple depuis des procédures stockées) est désactivé.  
  
 La valeur par défaut de cette propriété est False, qui indique que l'emprunt d'identité du client est activé.  
  
 `BuiltinAdminsAreServerAdmins`  
 Propriété booléenne qui indique si les membres du groupe des administrateurs de la machine locale sont des administrateurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 `ServiceAccountIsServerAdmin`  
 Propriété booléenne qui indique si le compte de service est un administrateur de serveur.  
  
 La valeur par défaut de cette propriété est True, qui indique que le compte de service est un administrateur de serveur.  
  
 `ErrorMessageMode`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataProtection\ RequiredProtectionLevel`  
 Propriété entière de 32 bits signée qui définit le niveau de protection nécessaire pour toutes les demandes des clients. Cette propriété peut prendre l'une des valeurs répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|*0*|Aucun, texte clair autorisé.|  
|*1*|(Valeur par défaut) Chiffrement requis, pas de journalisation en texte clair.|  
|*2*|Demandes en texte clair autorisées, mais seulement avec des signatures (protection plus faible que le chiffrement).|  
  
 `AdministrativeDataProtection\ RequiredProtectionLevel`  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du serveur dans Analysis Services](server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
