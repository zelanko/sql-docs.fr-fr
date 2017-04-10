---
title: "Propri&#233;t&#233;s du serveur de distribution, Serveurs de publication | Microsoft Docs"
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
  - "sql13.rep.configdistwizard.distproperties.publishers.f1"
helpviewer_keywords: 
  - "boîte de dialogue Propriétés du serveur de distribution"
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Propri&#233;t&#233;s du serveur de distribution, Serveurs de publication
  La page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution** vous permet de faire en sorte que les serveurs de publication utilisent ce serveur de distribution. Vous pouvez également définir les propriétés associées à ces serveurs de publication. Notez que l'activation d'un serveur de publication pour utiliser ce serveur en tant que serveur de distribution distant ne fait pas de ce serveur un serveur de publication. Vous devez vous connecter au serveur de publication, le configurer pour la publication, et choisir ce serveur comme distributeur. Vous pouvez configurer le serveur de publication et choisir un serveur de distribution à l'aide de l'Assistant Nouvelle publication.  
  
## Options  
 **Serveurs de publication**  
 Sélectionnez les serveurs autorisés à utiliser ce serveur de distribution. Cliquez sur le bouton des propriétés **(...)** en regard d’un éditeur pour afficher et définir des propriétés supplémentaires.  
  
 **Ajouter**  
 Si le serveur que vous souhaitez autoriser n’est pas répertorié, cliquez sur **Add** pour ajouter un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication ou le serveur de publication Oracle à la liste des serveurs de publication disponibles. Si le serveur ajouté est le premier à utiliser ce serveur de distribution en tant que serveur de distribution distant, vous serez invité à fournir un mot de passe de lien d'administration.  
  
 **Mot de passe du lien d'administration**  
 Permet de spécifier ou de mise à jour le mot de passe pour la connexion de réplication établit entre le serveur de publication et le serveur de distribution distant à l’aide du **distributor_admin** connexion :  
  
-   Si le serveur de distribution sert uniquement au niveau local, ce mot de passe est généré de manière aléatoire et configuré automatiquement.  
  
-   Si le serveur de distribution possède déjà un serveur de publication distant, un mot de passe a déjà été fourni sur cette page ou la page **Mot de passe du serveur de distribution** de l'Assistant Configuration de la distribution.  
  
-   Si vous activez le premier serveur de publication distant pour ce serveur de distribution, vous serez invité à entrer un mot de passe.  
  
 Pour plus d’informations sur la sécurité des serveurs de distribution, consultez [sécuriser le serveur de distribution](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  