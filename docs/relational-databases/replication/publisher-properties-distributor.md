---
title: "Propri&#233;t&#233;s du serveur de publication - Serveur de distribution | Microsoft Docs"
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
  - "sql13.rep.configdistwizard.distpubproperties.f1"
helpviewer_keywords: 
  - "Propriétés du serveur de publication (boîte de dialogue)"
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Propri&#233;t&#233;s du serveur de publication - Serveur de distribution
  La boîte de dialogue **Propriétés du serveur de publication** permet d'afficher et de modifier les propriétés associées à la relation existant entre le serveur de publication et son serveur de distribution.  
  
## Options  
 **Connexion de l'agent au serveur de publication**  
 Permet d'ajouter le contexte selon lequel les agents suivants établissent les connexions du serveur de distribution au serveur de publication :  
  
-   l'Agent de lecture de la file d'attente propre aux publications transactionnelles autorisant les abonnements de mise à jour dans la file d'attente ;  
  
-   l'Agent d'instantané et l'Agent de lecture du journal pour les publications Oracle.  
  
 Choisissez l'option **Imiter le compte de processus de l'Agent** afin d'établir des connexions au serveur de publication grâce au contexte du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows fourni et sous lequel ces agents doivent s'exécuter, ou bien choisissez **Authentification SQL Server**et saisissez alors une valeur pour chacun des champs **Connexion** et **Mot de passe**. Nous vous recommandons de sélectionner plutôt l'option **Imiter le compte de processus de l'Agent**. Pour plus d’informations sur la sécurité de l’agent, consultez [modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Les comptes Windows sous lesquels ces agents s'exécutent sont précisés dans l'Assistant Nouvelle publication. Ces comptes peuvent être modifiés de l'une des façons suivantes :  
  
-   dans la boîte de dialogue **Propriétés du serveur de distribution** , en ce qui concerne l'Agent de lecture de la file d'attente ;  
  
-   dans la boîte de dialogue **Propriétés du serveur de publication** , dans le cas de l'Agent d'instantané et de l'Agent de lecture du journal.  
  
 **Divers**  
 Les propriétés **Type de serveur de publication** et **nom de base de données de Distribution** sont en lecture seule. La propriété **Dossier d'instantanés par défaut** est cependant modifiable. Pour plus d’informations sur le dossier de capture instantanée, consultez [sécuriser le dossier de capture instantanée](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Référence des propriétés de & #40 ; Réplication & #41 ;](../../relational-databases/replication/properties-reference-replication.md)  
  
  