---
title: "R&#233;f&#233;rence de l&#39;interface utilisateur de la bo&#238;te de dialogue Exporter un package | Microsoft Docs"
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
  - "sql13.dts.dtsserver.exportpackage.f1"
helpviewer_keywords: 
  - "Exporter un package, boîte de dialogue"
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# R&#233;f&#233;rence de l&#39;interface utilisateur de la bo&#238;te de dialogue Exporter un package
  Utilisez la boîte de dialogue **Exporter un package**, disponible dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], pour exporter un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] vers un autre emplacement et éventuellement modifier son niveau de protection.  
  
## Options  
 **Emplacement du package**  
 Sélectionnez le type de stockage vers lequel exporter le package. Les options suivantes sont disponibles :  
  
 **SQL Server**  
  
 **Système de fichiers**  
  
 **Magasin de packages SSIS**  
  
 **Server**  
 Tapez le nom d’un serveur ou sélectionnez-en un dans la liste.  
  
 **Authentification**  
 Sélectionnez l'authentification Windows ou l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option est disponible uniquement si l’emplacement de stockage est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Dans la mesure du possible, utilisez l’authentification Windows.  
  
 **Type d'authentification**  
 Sélectionnez un type d'authentification.  
  
 **Nom d'utilisateur**  
 Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], entrez un nom d’utilisateur.  
  
 **Mot de passe**  
 Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], entrez un mot de passe.  
  
 **Chemin d'accès au package**  
 Tapez le chemin du package ou cliquez sur le bouton Parcourir **(…)** pour rechercher le dossier dans lequel stocker le package.  
  
 **Niveau de protection**  
 Cliquez sur le bouton Parcourir **(…)** et mettez à jour le niveau de protection dans la boîte de dialogue **Niveau de protection du package**. Pour plus d’informations, consultez [Boîte de dialogue Niveau de protection du package](../../integration-services/packages/package-and-project-protection-level-dialog-box.md).  
  
## Voir aussi  
 [Enregistrer une copie du package](../Topic/Save%20Copy%20of%20Package.md)   
 [Référence de l'interface utilisateur de la boîte de dialogue Importer un package](../../integration-services/service/import-package-dialog-box-ui-reference.md)   
 [Enregistrer des packages](../../integration-services/save-packages.md)   
 [Importer et exporter des packages &#40;SSIS Service&#41;](../../integration-services/service/import-and-export-packages-ssis-service.md)  
  
  