---
title: "Dossier d&#39;instantan&#233;s | Microsoft Docs"
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
  - "sql13.rep.replicationutilities.specifysnapshotfolder.f1"
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# Dossier d&#39;instantan&#233;s
  La page **Dossier d'instantanés** figure dans l'Assistant Configuration de la distribution et l'Assistant Nouvelle publication. L’emplacement que vous spécifiez pour le dossier de capture instantanée sera utilisé comme valeur par défaut pour tous les éditeurs activé dans cet Assistant (le dossier de capture instantanée par défaut ne s’applique pas aux serveurs de publication qui sont ensuite activés à l’aide de la **des propriétés de serveur de distribution** boîte de dialogue). Vous pouvez changer ce dossier par défaut pour n'importe quel serveur de publication dans la page **Serveurs de publication** de l'Assistant Configuration de la distribution ou la boîte de dialogue **Propriétés du serveur de distribution** .  
  
 Le dossier d'instantanés correspond à un simple répertoire que vous définissez sous la forme d'un partage ; les agents qui lisent et écrivent dans le dossier doivent disposer des autorisations suffisantes pour pouvoir y accéder. Pour plus d’informations sur la sécurisation du dossier de manière appropriée, consultez [sécuriser le dossier de capture instantanée](../../relational-databases/replication/security/secure-the-snapshot-folder.md). Avant d'implémenter la réplication, vérifiez que les agents de réplication peuvent se connecter au dossier d'instantanés. Connectez-vous sous le compte qu'utilisera chaque agent et essayez ensuite d'accéder au dossier d'instantanés.  
  
## Options  
 **Dossier d'instantanés**  
 Entrez le chemin d'accès au dossier où vous souhaitez stocker les fichiers d'instantanés.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'utiliser un partage réseau comme emplacement pour le dossier d'instantanés. Chemins d’accès locaux (ceux qui commencent par une lettre de lecteur, tel que C:\\) ne sont pas accessibles aux agents sur d’autres ordinateurs.  
  
## Voir aussi  
 [Autres emplacements du dossier d'instantané](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  