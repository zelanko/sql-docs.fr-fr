---
title: "Propriétés de sécurité | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0233cd9c2e9eff5cc776b921e092206524546a52
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="security-properties"></a>Propriétés de sécurité
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de sécurité du serveur répertoriées dans le tableau ci-dessous. Pour plus d’informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **S'applique à :** mode serveur multidimensionnel et tabulaire  
  
## <a name="properties"></a>Propriétés  
 **RequireClientAuthentication**  
 Propriété booléenne qui indique si le client doit être authentifié.  
  
 La valeur par défaut de cette propriété est True, qui indique que le client doit être authentifié.  
  
 **SecurityPackageList**  
 Propriété de type chaîne qui contient une liste (séparée par des virgules) des packages SSPI utilisés par le serveur pour l'authentification des clients.  
  
 **DisableClientImpersonation**  
 Propriété booléenne qui indique si l'emprunt d'identité du client (par exemple depuis des procédures stockées) est désactivé.  
  
 La valeur par défaut de cette propriété est False, qui indique que l'emprunt d'identité du client est activé.  
  
 **BuiltinAdminsAreServerAdmins**  
 Propriété booléenne qui indique si les membres du groupe des administrateurs de la machine locale sont des administrateurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 **ServiceAccountIsServerAdmin**  
 Propriété booléenne qui indique si le compte de service est un administrateur de serveur.  
  
 La valeur par défaut de cette propriété est True, qui indique que le compte de service est un administrateur de serveur.  
  
 **ErrorMessageMode**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **DataProtection\ RequiredProtectionLevel**  
 Propriété entière de 32 bits signée qui définit le niveau de protection nécessaire pour toutes les demandes des clients. Cette propriété peut prendre l'une des valeurs répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0*|Aucun, texte clair autorisé.|  
|*1*|(Valeur par défaut) Chiffrement requis, pas de journalisation en texte clair.|  
|*2*|Demandes en texte clair autorisées, mais seulement avec des signatures (protection plus faible que le chiffrement).|  
  
 **AdministrativeDataProtection\ RequiredProtectionLevel**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
