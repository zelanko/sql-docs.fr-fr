---
title: "Acc&#233;der au service Integration Services | Microsoft Docs"
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
  - "packages SSIS, sécurité"
  - "affichage des packages en cours d’exécution"
  - "affichage des packages en cours d'exécution"
  - "sécurité [Integration Services], exécution des packages"
  - "packages [Integration Services], sécurité"
  - "packages en cours d'exécution"
  - "Integration Services (packages), sécurité"
  - "SQL Server Integration Services (packages), sécurité"
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Acc&#233;der au service Integration Services
  Les niveaux de protection des packages peuvent définir des restrictions quant aux utilisateurs autorisés à modifier et exécuter un package. Une protection supplémentaire est nécessaire pour limiter les utilisateurs autorisés à afficher la liste des packages actuellement en cours d’exécution sur un serveur et ceux qui peuvent arrêter les packages en cours d’exécution dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilise le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]pour établir la liste des packages en cours d’exécution. Les membres du groupe Administrateurs de Windows peuvent afficher et arrêter tous les packages en cours d'exécution. Les utilisateurs n'appartenant pas au groupe Administrateurs de Windows ne peuvent afficher et arrêter que les packages qu'ils ont démarrés.  
  
 Il est important de restreindre l'accès aux ordinateurs qui exécutent un service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], notamment un service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui peut énumérer des dossiers distants. Tout utilisateur authentifié peut demander l'énumération des packages. Même si le service ne trouve pas le service, il énumère les dossiers. Ces noms de dossiers peuvent être utilisés par un utilisateur malveillant. Si un administrateur a configuré le service pour qu'il énumère les dossiers sur un ordinateur distant, les utilisateurs peuvent également voir des noms de dossiers qu'ils ne pourraient pas voir en temps normal.  
  
  