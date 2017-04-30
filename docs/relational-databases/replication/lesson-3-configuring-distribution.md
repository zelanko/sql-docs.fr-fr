---
title: "Leçon 3 : Configuration de la distribution | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e582c5fb7853c69a083755a944bd3922d0d4c5af
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-3-configuring-distribution"></a>Leçon 3 : Configuration de la distribution
Dans cette leçon, vous allez configurer la distribution sur le serveur de publication et définir les autorisations requises sur les bases de données de publication et de distribution. Si vous avez déjà configuré le serveur de distribution, vous devez d'abord désactiver la publication et la distribution avant de commencer cette leçon. Ne procédez pas ainsi si vous devez conserver une topologie de réplication existante.  
  
La configuration d'un serveur de publication avec un serveur de distribution distant dépasse le cadre de ce didacticiel.  
  
### <a name="configuring-distribution-at-the-publisher"></a>Configuration de la distribution sur le serveur de publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Cliquez avec le bouton droit sur le dossier **Réplication** , puis cliquez sur **Configurer la distribution**.  
  
    > [!NOTE]  
    > Si vous êtes connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de **localhost** au lieu du nom du serveur réel, un avertissement vous indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas se connecter au serveur **'localhost'**. Cliquez sur **OK** dans la boîte de dialogue d'avertissement. Dans la boîte de dialogue **Se connecter au serveur** , remplacez le **Nom du serveur** , qui indique **localhost** , par le nom de votre serveur. Cliquez sur **Se connecter**.  
  
    L'Assistant Configuration de la distribution démarre.  
  
3.  Dans la page **Serveur de distribution** , sélectionnez ‘nom_serveur’ agit comme son propre serveur de distribution ; SQL Server crée une base de données de distribution et un journal**, puis cliquez sur **Suivant**.  
  
4.  Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne s’exécute pas, dans la page de démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Agent**, sélectionnez **Oui**, configurez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour qu’il démarre automatiquement. Cliquez sur **Suivant**.  
  
5.  Entrez **\\\\**\<*nom_ordinateur>***\repldata** dans la zone de texte **Dossier d’instantanés**, où \<*nom_ordinateur>* désigne le serveur de publication, puis cliquez sur **Suivant**.  
  
6.  Acceptez les valeurs par défaut sur les pages restantes de l'Assistant.  
  
7.  Cliquez sur **Terminer** pour activer la distribution.  
  
### <a name="setting-database-permissions-at-the-publisher"></a>Définition des autorisations de base de données sur le serveur de publication  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis sélectionnez **Nouvelle connexion**.  
  
2.  Dans la page **Général**, cliquez sur **Rechercher**, entrez \<*nom_ordinateur>***\repl_snapshot** dans la zone **Entrez le nom de l’objet à sélectionner**, où \<*nom_ordinateur>* désigne le serveur de publication local, cliquez sur **Vérifier les noms**, puis cliquez sur **OK**.  
  
3.  Sur la page **Mappage de l'utilisateur** , dans la liste **Utilisateurs mappés à cette connexion** , sélectionnez les bases de données **distribution** et [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
    Dans la liste **Appartenance au rôle de base de données** sélectionnez le rôle **db_owner** pour la connexion pour les deux bases de données.  
  
4.  Cliquez sur **OK** pour créer la connexion.  
  
5.  Répétez les étapes 1 à 4 pour créer une connexion pour le compte local repl_logreader. Cette connexion doit aussi être mappée aux utilisateurs membres du rôle de base de données fixe **db_owner** des bases de données de **distribution** et **AdventureWorks** .  
  
6.  Répétez les étapes 1 à 4 pour créer une connexion pour le compte local repl_distribution. Cette connexion doit être mappée à un utilisateur membre du rôle de base de données fixe **db_owner** de la base de données de **distribution** .  
  
7.  Répétez les étapes 1 à 4 pour créer une connexion pour le compte local repl_merge. Cette connexion doit avoir les mappages d'utilisateur des bases de données de **distribution** et **AdventureWorks** .  
  
## <a name="see-also"></a>Voir aussi  
[Configurer la distribution](../../relational-databases/replication/configure-distribution.md)  
[Modèle de sécurité de l'Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md)  
  
  
  

