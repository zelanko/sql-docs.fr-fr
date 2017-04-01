---
title: "Cr&#233;ation de scripts de r&#233;plication | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scripts [réplication SQL Server], objets de réplication"
  - "création de scripts de réplication de fusion [réplication SQL Server]"
  - "réplication [SQL Server], création de scripts"
  - "réplication de capture instantanée [SQL Server], scripts"
  - "scripts [réplication SQL Server]"
  - "réplication transactionnelle, scripts"
ms.assetid: e50fac44-54c0-470c-a4ea-9c111fa4322b
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Cr&#233;ation de scripts de r&#233;plication
  Tous les composants de réplication dans une topologie doivent faire l'objet d'un script et s'intégrer dans un plan de récupération des données en cas de sinistre ; les scripts peuvent également être utilisés pour automatiser des tâches répétitives. Un script contient les procédures stockées système Transact-SQL nécessaires pour mettre en œuvre le ou les composants de réplication définis dans des scripts, tels qu'une publication ou un abonnement. Les scripts peuvent être créés dans l’Assistant (par exemple, l’Assistant Nouvelle Publication) ou dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] après avoir créé un composant. Vous pouvez afficher, modifier et exécuter le script à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou **sqlcmd**. Les scripts peuvent être stockés avec les fichiers de sauvegarde dans le cas où la topologie de réplication doit être reconfigurée.  
  
 Un nouveau script doit être généré pour un composant si des modifications sont apportées à ses propriétés. Si vous utilisez des procédures stockées personnalisées avec la réplication transactionnelle, une copie de chaque procédure doit être stockée avec les scripts ; la copie doit être mise à jour si la procédure change (les procédures sont généralement mises à jour suite à des modifications de schéma ou à des modifications des conditions requises par l'application). Pour plus d’informations sur les procédures personnalisées, consultez [spécifier comment les modifications sont propagées des Articles transactionnels](../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
 Pour les publications de fusion qui utilisent des filtres paramétrés, les scripts de publication contiennent l'appel de la procédure stockée pour créer des partitions de données. Le script fournit une référence pour les partitions créées et un moyen permettant de recréer si nécessaire une ou plusieurs partitions.  
  
## Exemple d'automatisation d'une tâche avec des scripts  
 Considérons [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], qui met en œuvre la réplication de fusion pour distribuer des données à sa force de vente distante. Un commercial télécharge toutes les données qui se rapportent aux clients de son territoire, à l'aide d'abonnements par extraction de données (pull). En mode déconnecté, les représentants commerciaux mettent à jour des données et entrent de nouveaux clients et de nouvelles commandes. [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] employant plus de 50 représentants commerciaux sur des territoires différents, il serait donc très long de créer les différents abonnements sur chaque Abonné avec l'Assistant Nouvel abonnement. À la place, l'administrateur de réplication peut procéder selon les étapes suivantes :  
  
1.  Configurez les publications de fusion nécessaires avec des partitions basées sur le représentant commercial ou son territoire.  
  
2.  Créez un abonnement par extraction de données (pull) pour un Abonné.  
  
3.  Générez un script basé sur cet abonnement par extraction de données (pull).  
  
4.  Modifiez le script, en changeant des valeurs comme le nom de l'Abonné.  
  
5.  Exécutez le script sur plusieurs Abonnés pour générer les abonnements par extraction de données (pull) requis.  
  
## Objets de réplication Script  
 Générer un script des objets de réplication à partir des Assistants de réplication ou de la **réplication** dossier [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si vous générez des scripts à partir des Assistants, vous pouvez opter pour la création d'objets et leur intégration dans un script ou pour la génération de scripts seuls.  
  
> [!IMPORTANT]  
>  Tous les mots de passe sont définis dans le script avec la valeur NULL. Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous stockez des informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher tout accès non autorisé.  
  
 Pour plus d'informations sur l'utilisation des Assistants de réplication, consultez :  
  
-   [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
-   [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)  
  
-   [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)  
  
#### Pour générer un script pour un objet à partir d'un Assistant de réplication  
  
1.  Sur le **Actions de l’Assistant** page de l’Assistant, sélectionnez la case à cocher appropriée pour l’Assistant :  
  
    -   **Générer un fichier de script comportant les étapes de création d'une publication**  
  
    -   **Générer un fichier de script comportant les étapes de création d'une ou de plusieurs publications**  
  
    -   **Générer un fichier de script comportant les étapes de configuration de la distribution**  
  
2.  Spécifier des options sur la **Propriétés du fichier Script** page.  
  
3.  Terminez l'Assistant.  
  
#### Pour générer un script pour un objet à partir de Management Studio  
  
1.  Connectez-vous au serveur de distribution, au serveur de publication ou à l'Abonné dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le **réplication** dossier, puis développez le **Publications locales** dossier ou **abonnements locaux** dossier.  
  
3.  Cliquez sur une publication ou abonnement, puis cliquez sur **Générer des Scripts**.  
  
4.  Spécifiez les options dans la **Générer un Script SQL - \< ReplicationObject>** boîte de dialogue.  
  
5.  Cliquez sur **Script au fichier**.  
  
6.  Entrez un nom de fichier dans le **emplacement du fichier de Script** boîte de dialogue, puis cliquez sur **Enregistrer**. Un message d'état est affiché.  
  
7.  Cliquez sur **OK**, puis cliquez sur **Fermer**.  
  
#### Pour générer un script pour plusieurs objets à partir de Management Studio  
  
1.  Connectez-vous au serveur de distribution, au serveur de publication ou à l'Abonné dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Cliquez sur le **réplication** puis cliquez sur **Générer des Scripts**.  
  
3.  Spécifiez les options dans la **Générer un Script SQL** boîte de dialogue.  
  
4.  Cliquez sur **Script au fichier**.  
  
5.  Entrez un nom de fichier dans le **emplacement du fichier de Script** boîte de dialogue, puis cliquez sur **Enregistrer**. Un message d'état est affiché.  
  
6.  Cliquez sur **OK, puis** cliquez sur **Fermer**.  
  
  