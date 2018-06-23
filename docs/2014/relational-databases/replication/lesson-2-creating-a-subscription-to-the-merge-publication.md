---
title: 'Leçon 2 : Création d’un abonnement à la publication de fusion | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ad258c2be4e7df3ff353a9fd1a1f9e7c083991d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051924"
---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a>Leçon 2 : Création d'un abonnement à la publication de fusion
  Dans cette leçon, vous allez créer l’abonnement à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Puis, vous définirez les autorisations sur la base de données d'abonnement et génèrerez manuellement l'instantané filtré des données du nouvel abonnement. Pour effectuer cette leçon, vous devez avoir terminé la leçon précédente, [Leçon 1 : Publication de données à l’aide de la réplication de fusion](lesson-1-publishing-data-using-merge-replication.md).  
  
### <a name="to-create-the-subscription"></a>Pour créer l'abonnement  
  
1.  Connectez-vous à l’abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, développez le dossier **Réplication** , cliquez avec le bouton droit sur le dossier **Abonnements locaux** , puis choisissez **Nouvel abonnement**.  
  
     L'Assistant Nouvel abonnement démarre.  
  
2.  Dans la page **Publication** , choisissez **Rechercher un serveur de publication SQL** dans la liste **Serveur de publication** .  
  
3.  Dans la boîte de dialogue **Connect Se connecter au serveur** , entrez le nom de l’instance du serveur de publication dans la zone **Nom du serveur** , puis cliquez sur **Se connecter**.  
  
4.  Cliquez sur **AdvWorksSalesOrdersMerge**, puis sur **Suivant**.  
  
5.  Dans la page Emplacement de l’Agent de fusion, cliquez sur **Exécuter chaque agent sur son Abonné**, puis cliquez sur **Suivant**.  
  
6.  Dans la page abonnés, sélectionnez le nom de l’instance de l’abonné et sous **base de données d’abonnement**, sélectionnez  **\<nouvelle base de données >** à partir de la liste.  
  
7.  Dans la boîte de dialogue **Nouvelle base de données** , entrez **SalesOrdersReplica** dans la zone **Nom de la base de données** , cliquez sur **OK**, puis cliquez sur **Suivant**.  
  
8.  Dans la page Sécurité de l’Agent de fusion, cliquez sur le bouton de sélection (**…**), entrez \<*nom_ordinateur>\repl_merge** dans la zone **Compte de processus**, fournissez le mot de passe de ce compte, cliquez sur **OK**, sur **Suivant**, et une nouvelle fois sur **Suivant**.  
  
9. Dans la page Initialiser les abonnements, sélectionnez **Lors de la première synchronisation** dans la liste **À quel moment** , cliquez sur **Suivant**, puis une nouvelle fois sur **Suivant** .  
  
10. Dans la page valeurs de HOST_NAME, entrez la valeur `adventure-works\pamela0` dans les **valeur de HOST_NAME** zone, puis cliquez sur **Terminer**.  
  
11. Cliquez à nouveau sur **Terminer** et, une fois l’abonnement créé, cliquez sur **Fermer**.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Définition des autorisations de base de données sur l'Abonné  
  
1.  Connectez-vous à l’Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez **Bases de données**, **SalesOrdersReplica**et **Sécurité**, cliquez avec le bouton droit sur **Utilisateurs**, puis choisissez **Nouvel utilisateur**.  
  
2.  Dans la page **Général**, entrez \<*nom_ordinateur>***\repl_merge** dans la zone **Nom d’utilisateur**, cliquez sur le bouton de sélection (**…**), cliquez sur **Parcourir**, sélectionnez \<*nom_ordinateur>***\repl_merge**, cliquez sur **OK**, sur **Vérifier les noms**, et à nouveau sur **OK**.  
  
3.  Dans **Appartenance au rôle de base de données**, sélectionnez **db_owner**, puis cliquez sur **OK** pour créer l’utilisateur.  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>Pour créer l'instantané filtré des données de l'abonnement  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis le dossier **Réplication** .  
  
2.  Dans le dossier **Publications locales** , cliquez avec le bouton droit sur la publication **AdvWorksSalesOrdersMerge** , puis cliquez sur **Propriétés**.  
  
     La boîte de dialogue **Propriétés de la publication** s’affiche.  
  
3.  Sélectionnez la page **Partitions de données** , puis cliquez sur **Ajouter**.  
  
4.  Dans le **ajouter une Partition de données** boîte de dialogue, tapez `adventure-works\pamela0` dans les **valeur de HOST_NAME** zone, puis cliquez sur **OK**.  
  
5.  Sélectionnez la partition nouvellement ajoutée, cliquez sur **Générer les instantanés sélectionnés maintenant**, puis sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez créé avec succès un abonnement à la publication de fusion et généré l'instantané filtré pour la partition de données du nouvel abonnement de telle sorte qu'il soit disponible lors de l'initialisation de l'abonnement. Ensuite, vous allez accorder des droits à l'Agent de fusion sur la base de données d'abonnement et exécuter l'Agent de fusion pour démarrer la synchronisation et initialiser l'abonnement. Consultez [Leçon 3 : Synchronisation de l’abonnement et de la publication de fusion](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Subscribe to Publications](subscribe-to-publications.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Instantanés des publications de fusion avec des filtres paramétrés](snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  