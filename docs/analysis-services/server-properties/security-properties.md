---
title: "Propri&#233;t&#233;s de s&#233;curit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "sécurité [Analysis Services], propriétés"
  - "SecurityPackageList, propriété"
  - "BuiltinAdminsAreServerAdmins, propriété"
  - "DisableClientImpersonation, propriété"
  - "ErrorMessageMode, propriété"
  - "RequiredProtectionLevel, propriété"
  - "ServiceAccountIsServerAdmin, propriété"
  - "RequireClientAuthentication, propriété"
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 15
---
# Propri&#233;t&#233;s de s&#233;curit&#233;
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge les propriétés de sécurité du serveur répertoriées dans le tableau ci-dessous. Pour plus d’informations sur les autres propriétés de serveur et la façon de les configurer, consultez [Propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **S'applique à :** mode serveur multidimensionnel et tabulaire  
  
## Propriétés  
 **RequireClientAuthentication**  
 Propriété booléenne qui indique si le client doit être authentifié.  
  
 La valeur par défaut de cette propriété est True, qui indique que le client doit être authentifié.  
  
 **SecurityPackageList**  
 Propriété de type chaîne qui contient une liste (séparée par des virgules) des packages SSPI utilisés par le serveur pour l'authentification des clients.  
  
 **DisableClientImpersonation**  
 Propriété booléenne qui indique si l'emprunt d'identité du client (par exemple depuis des procédures stockées) est désactivé.  
  
 La valeur par défaut de cette propriété est False, qui indique que l'emprunt d'identité du client est activé.  
  
 **BuiltinAdminsAreServerAdmins**  
 Propriété booléenne qui indique si les membres du groupe des administrateurs de la machine locale sont des administrateurs [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
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
  
## Voir aussi  
 [propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Déterminer le mode serveur d'une instance Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  