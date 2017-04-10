---
title: "Enregistrer des packages | Microsoft Docs"
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
  - "sql13.dts.designer.savecopyas.f1"
helpviewer_keywords: 
  - "packages Integration Services, enregistrement"
  - "packages [Integration Services], enregistrement"
  - "enregistrement des packages"
  - "packages SSIS, enregistrement"
  - "packages SQL Server Integration Services, enregistrement"
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 47
---
# Enregistrer des packages
  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], vous créez des packages à l’aide du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] et vous les enregistrez dans le système de fichiers sous forme de fichiers XML (fichiers .dtsx). Vous pouvez également enregistrer des copies du fichier XML des packages dans la base de données msdb dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou dans le magasin de packages. Le magasin de packages représente les dossiers de l’emplacement du système de fichiers gérés par le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 Si vous enregistrez un package dans le système de fichiers, vous pouvez utiliser par la suite le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour importer le package dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou dans le magasin de packages. Pour plus d’informations, consultez [Importer et exporter des packages &#40;Service SSIS&#41;](../integration-services/service/import-and-export-packages-ssis-service.md).  
  
 Vous pouvez également utiliser un utilitaire d’invite de commandes, **dtutil**, pour copier un package entre le système de fichiers et msdb. Pour plus d’informations, consultez [dtutil Utility](../integration-services/dtutil-utility.md).  
  
### Pour enregistrer un package  
  
-   [Enregistrer un package dans le système de fichiers](../Topic/Save%20a%20Package%20to%20the%20File%20System.md)  
  
-   [Enregistrer une copie d'un package](../Topic/Save%20a%20Copy%20of%20a%20Package.md)  
  
  