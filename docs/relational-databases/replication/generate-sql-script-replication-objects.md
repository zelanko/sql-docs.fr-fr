---
title: "G&#233;n&#233;rer un script SQL (objets de r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.generatesqlscript.f1"
helpviewer_keywords: 
  - "boîte de dialogue Générer un script SQL"
ms.assetid: b7ccc34e-1c22-44b8-8eb5-f6423af3164e
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# G&#233;n&#233;rer un script SQL (objets de r&#233;plication)
  Un script de réplication contient les procédures stockées système [!INCLUDE[tsql](../../includes/tsql-md.md)] nécessaires à l'implémentation de composants de réplication en script, tels qu'une publication ou un abonnement. Tous les composants de réplication dans une topologie doivent faire l'objet d'un script et s'intégrer dans un plan de récupération des données en cas de sinistre ; les scripts peuvent également être utilisés pour automatiser des tâches répétitives. La réplication propose deux boîtes de dialogue spécifiques à l'écriture de scripts mettant en œuvre des objets de réplication :  
  
-   **Générer un Script SQL**, qui est disponible dans le menu contextuel de la **réplication** dossier et tous les sous-dossiers de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Cette boîte de dialogue vous permet de créer un script de tous les objets de réplication sur une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Générer un Script SQL \< nomobjet>**, qui est disponible dans le menu contextuel pour les publications et abonnements. Cette boîte de dialogue vous permet de générer des scripts d'objets individuels.  
  
 Ces boîtes de dialogue génèrent des scripts d'objets sur une instance unique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ils ne se connectent pas à d'autres instances pour permettre générer des scripts d'objets associés.  
  
## Options de la boîte de dialogue Générer un script SQL  
 **Propriétés du serveur de distribution**  
 Permet de générer des scripts de procédures stockées pour : activer ou désactiver le serveur de distribution, ajouter ou supprimer des serveurs de publication associés au serveur de distribution, et créer ou supprimer la base de données de distribution.  
  
 **Publications dans les sources de données suivantes**  
 Permet de générer des scripts de procédures stockées pour : activer ou désactiver la publication, et créer ou supprimer des publications, des articles, des abonnements par extraction et des travaux de réplication.  
  
 **Abonnements dans les sources de données suivantes**  
 Permet de générer des scripts de procédures stockées afin de créer ou de supprimer des abonnements extraits et des travaux de réplication.  
  
 **Pour créer ou activer les composants** et **pour supprimer ou désactiver les composants**  
 Permet d'indiquer si le script doit inclure des commandes de création ou de suppression d'un objet de réplication. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d’utiliser la boîte de dialogue pour créer un ensemble de scripts pour l’activation et la désactivation de composants.  
  
 **Travaux de réplication**  
 Permet de générer des scripts de travaux de réplication en complément des scripts d'appels de procédures stockées. Cette option n'est disponible que lors de la génération de scripts à partir d'un serveur de distribution.  
  
 Les procédures stockées de réplication créent les travaux nécessaires lors de leur exécution ; il n'est donc pas requis de choisir cette option. Il peut toutefois s'avérer utile d'obtenir un enregistrement des travaux créés dans le cas où un seul travail devait être recréé.  
  
## Générer un Script SQL \< nomobjet> Options  
 **Pour créer ou activer les composants** et **pour supprimer ou désactiver les composants**  
 Permet d'indiquer si le script doit inclure des commandes de création ou de suppression d'un objet de réplication. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d’utiliser la boîte de dialogue Création d’un ensemble de scripts pour l’activation et la désactivation de composants.  
  
 **Travaux de réplication**  
 Cette option est disponible uniquement à partir de la **Générer un Script SQL** boîte de dialogue.  
  
## Voir aussi  
 [Création de scripts de réplication](../../relational-databases/replication/scripting-replication.md)  
  
  