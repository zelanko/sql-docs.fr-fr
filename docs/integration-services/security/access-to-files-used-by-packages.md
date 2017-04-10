---
title: "Acc&#233;der aux fichiers utilis&#233;s par des packages | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSIS (packages), sécurité"
  - "packages [Integration Services], sécurité"
  - "fichiers de configuration [Integration Services]"
  - "fichiers de point de contrôle"
  - "packages Integration Services, sécurité"
  - "journaux [Integration Services], sécurité"
  - "fichiers [Integration Services], sécurité"
  - "SQL Server Integration Services (packages), sécurité"
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Acc&#233;der aux fichiers utilis&#233;s par des packages
  Le niveau de protection de package ne protège pas les fichiers stockés en dehors du package. Il s'agit des fichiers suivants :  
  
-   Fichiers de configuration  
  
-   Fichiers de points de contrôle  
  
-   Fichiers journaux  
  
 Ces fichiers doivent être protégés séparément, notamment s'ils contiennent des informations sensibles.  
  
## Fichiers de configuration  
 Si une configuration contient des informations sensibles, telles que des informations de connexion et de mot de passe, vous devez penser à enregistrer la configuration dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou à utiliser une liste de contrôle d’accès pour limiter l’accès à l’emplacement ou au dossier de stockage des fichiers et pour autoriser l’accès uniquement à certains comptes. En règle générale, vous accordez l'accès aux comptes que vous autorisez à exécuter des packages et à ceux qui gèrent et résolvent les problèmes des packages, ce qui peut comprendre l'inspection du contenu des fichiers de configuration, des fichiers de point de contrôle et des fichiers journaux. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit le stockage le plus sécurisé, car il offre une protection aux niveaux du serveur et des bases de données. Pour enregistrer des configurations dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous utilisez le type de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour enregistrer dans le système de fichiers, vous utilisez le type de configuration XML.  
  
 Pour plus d’informations, consultez [Configurations de package](../../integration-services/packages/package-configurations.md), [Créer des configurations de package](../../integration-services/packages/create-package-configurations.md) et [Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
## Fichiers de point de contrôle  
 De même, si le fichier de point de contrôle utilisé par le package contient des informations sensibles, vous devez utiliser une liste de contrôle d'accès pour sécuriser l'emplacement ou le dossier de stockage du fichier. Les fichiers de points de contrôle contiennent des informations d'état relatives à la progression du package, ainsi que les valeurs actuelles de certaines variables. Par exemple, le package peut inclure une variable personnalisée qui contient un numéro de téléphone. Pour plus d'informations, consultez [Restart Packages by Using Checkpoints](../../integration-services/packages/restart-packages-by-using-checkpoints.md).  
  
## Fichiers journaux  
 Les entrées de journaux qui sont écrites dans le système de fichiers doivent également être sécurisées au moyen d'une liste de contrôle d'accès. Elles peuvent aussi être stockées dans des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et protégées par la sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les entrées de journaux peuvent inclure des informations sensibles. Par exemple, si le package contient une tâche d'exécution SQL qui construit une instruction SQL faisant référence à un numéro de téléphone, l'entrée de journal de l'instruction SQL inclut le numéro de téléphone. L'instruction SQL peut également révéler des informations confidentielles relatives à des noms de tables et de colonnes dans des bases de données. Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md).  
  
  