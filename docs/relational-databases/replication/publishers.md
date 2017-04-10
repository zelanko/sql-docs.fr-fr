---
title: "Serveurs de publication | Microsoft Docs"
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
  - "sql13.rep.configuredistributionwizard.enablepublishers.f1"
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Serveurs de publication
  Vous pouvez autoriser les autres serveurs de publication à utiliser ce serveur de distribution. Notez que l'activation d'un serveur de publication pour utiliser ce serveur en tant que serveur de distribution distant ne fait pas de ce serveur un serveur de publication. Vous devez vous connecter au serveur de publication, le configurer pour la publication, et choisir ce serveur comme distributeur. Vous pouvez configurer le serveur de publication et choisir un serveur de distribution à l'aide de l'Assistant Nouvelle publication.  
  
 Les serveurs, que vous sélectionnez en tant que serveurs de publication, utilisent la base de données de distribution spécifiée dans la page **Base de données de distribution** de cet Assistant. Si vous souhaitez utiliser une autre base de données de distribution, n'activez pas le serveur de publication. Utilisez plutôt la boîte de dialogue **Propriétés du serveur de distribution** pour ajouter des serveurs de publication après avoir terminé l'exécution de l'Assistant Configuration de la distribution.  
  
## Options  
 **Serveurs de publication**  
 Sélectionnez les serveurs autorisés à utiliser ce serveur de distribution. Cliquez sur le bouton des propriétés (**...**) en regard d’un éditeur pour afficher et définir des propriétés supplémentaires.  
  
 **Ajouter**  
 Si le serveur que vous souhaitez autoriser n’est pas répertorié, cliquez sur **Add** pour ajouter un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication ou le serveur de publication Oracle à la liste des serveurs de publication disponibles.  
  
## Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)  
  
  