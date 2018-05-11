---
title: Propriétés de sécurité | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f6648facaa1fdb1aa750ca85a5e2ba8ba2a01c52
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="security-properties"></a>Propriétés de sécurité
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de sécurité du serveur répertoriées dans le tableau ci-dessous. Pour plus d’informations sur les autres propriétés de serveur et sur la façon de les configurer, consultez [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
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
 Propriété entière de 32 bits signée qui définit le niveau de protection nécessaire pour toutes les demandes des clients. Cette propriété peut prendre l'une des valeurs répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*0*|Aucun, texte clair autorisé.|  
|*1*|(Valeur par défaut) Chiffrement requis, pas de journalisation en texte clair.|  
|*2*|Demandes en texte clair autorisées, mais seulement avec des signatures (protection plus faible que le chiffrement).|  
  
 **AdministrativeDataProtection\ RequiredProtectionLevel**  
 Propriété avancée que vous ne devez pas modifier, sauf si vous bénéficiez de l'assistance du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d’une instance Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
