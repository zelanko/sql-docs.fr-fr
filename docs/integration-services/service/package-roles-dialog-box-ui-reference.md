---
title: "R&#233;f&#233;rence de l&#39;interface utilisateur de la bo&#238;te de dialogue R&#244;les de package | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.dtsserver.packageroles.f1"
helpviewer_keywords: 
  - "Rôles de package, boîte de dialogue"
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# R&#233;f&#233;rence de l&#39;interface utilisateur de la bo&#238;te de dialogue R&#244;les de package
  Utilisez la boîte de dialogue **Rôles de package**, disponible dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], pour spécifier les rôles au niveau de la base de données qui possèdent un accès en lecture au package et les rôles au niveau de la base de données qui possèdent un accès en écriture au package. Les rôles au niveau de la base de données s’appliquent uniquement aux packages stockés dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**.  
  
 Pour en savoir plus sur les rôles au niveau de la base de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et leurs autorisations, consultez [Rôles Integration Services &#40;Service SSIS&#41;](../../integration-services/service/integration-services-roles-ssis-service.md).  
  
 Les rôles répertoriés dans la boîte de dialogue sont les rôles actuels de la base de données système **msdb** . Si aucun rôle n'est sélectionné, les rôles [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] par défaut s'appliquent. Par défaut, le rôle de lecteur inclut **db_ssisadmin**, **db_ssisoperator** et l’utilisateur qui a créé le package. Un utilisateur membre de l'un de ces rôles ou qui a créé les packages peut énumérer, consulter, exporter et exécuter des packages. Par défaut, le rôle de rédacteur inclut **db_ssisadmin** et l’utilisateur qui a créé le package. Un utilisateur membre de ce rôle et l'utilisateur qui a créé les packages peuvent importer, supprimer et modifier des packages.  
  
 La colonne **ownersid** de la table **sysssispackages** contient l'identificateur de sécurité unique de l'utilisateur qui a créé le package.  
  
## Options  
 **Nom du package**  
 Spécifiez le nom du package.  
  
 **Rôle Lecteur**  
 Sélectionnez un rôle dans la liste.  
  
 **Rôle Rédacteur**  
 Sélectionnez un rôle dans la liste.  
  
## Voir aussi  
 [Rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md)   
 [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](../../integration-services/security/security-overview-integration-services.md)  
  
  