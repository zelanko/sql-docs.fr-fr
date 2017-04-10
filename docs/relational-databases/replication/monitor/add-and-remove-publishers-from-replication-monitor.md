---
title: "Ajouter et supprimer des serveurs de publication &#224; partir du Moniteur de r&#233;plication | Microsoft Docs"
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
  - "Moniteur de réplication, ajout et suppression de serveurs de publication"
ms.assetid: fa36c4b4-bfa5-494e-92e3-07a02d7332c3
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Ajouter et supprimer des serveurs de publication &#224; partir du Moniteur de r&#233;plication
  Le serveur à partir duquel vous lancez le moniteur de réplication est automatiquement ajouté au moniteur s'il s'agit d'un serveur de publication. Serveurs de publication supplémentaires peuvent être ajoutés via le **Ajouter le serveur de publication** boîte de dialogue. Après l'ajout d'un serveur de publication, celui-ci est affiché dans le volet gauche du moniteur. Le **Mes serveurs de publication** groupe est inclus par défaut, mais vous pouvez créer des groupes pour gérer un ou plusieurs topologies de réplication. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Pour ajouter un serveur de publication SQL Server  
  
1.  Avec le bouton droit le **le moniteur de réplication** nœud ou un éditeur de nœud dans le volet gauche de groupe, puis cliquez sur **Ajouter le serveur de publication**.  
  
2.  Dans le **Ajouter le serveur de publication** boîte de dialogue, cliquez sur **Ajouter**, puis cliquez sur **Ajouter un éditeur SQL Server**.  
  
3.  Dans le **se connecter au serveur** boîte de dialogue, entrez le nom du serveur de publication, puis sélectionnez le type d’authentification. Si vous sélectionnez **l’authentification SQL Server**, entrez une connexion et un mot de passe. Les informations d'identification que vous spécifiez sont enregistrées par le moniteur de réplication pour se connecter à ce serveur dans le futur. Le compte Windows ou connexion SQL Server spécifiée doit être un membre de la **sysadmin** rôle serveur fixe ou un membre de la **replmonitor** rôle fixe de base de données dans la base de données de distribution.  
  
4.  Cliquez sur **Se connecter**. Si le serveur de publication utilise un serveur de distribution distant, vous devrez vous connecter au serveur de distribution dans le **se connecter au serveur** boîte de dialogue. Les informations d'identification que vous spécifiez sont enregistrées par le moniteur de réplication pour se connecter à ce serveur dans le futur. Le compte Windows ou connexion SQL Server spécifiée doit être un membre de la **sysadmin** rôle serveur fixe ou un membre de la **replmonitor** rôle fixe de base de données dans la base de données de distribution.  
  
5.  Le nom de l’éditeur et le distributeur sont affichés dans le **Analysez l’ou les éditeurs suivant** grille.  
  
6.  Pour spécifier des options d'actualisation et de connexion pour le serveur de publication , sélectionnez le serveur de publication dans la grille et modifiez les options comme vous le souhaitez. Pour plus d’informations sur les options d’actualisation, consultez [mise en cache, l’actualisation et performances du moniteur de réplication](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
7.  Sélectionnez le groupe sous lequel le serveur de publication doit être affiché dans le moniteur de réplication. Pour créer un nouveau groupe, cliquez sur **Nouveau groupe**, puis entrez un nom de groupe ; sélectionnez le groupe dans le **Afficher cet éditeur (s) dans le groupe suivant** liste.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Pour ajouter un serveur de publication Oracle  
  
1.  Avec le bouton droit le **le moniteur de réplication** nœud ou un éditeur de nœud dans le volet gauche de groupe, puis cliquez sur **Ajouter le serveur de publication**.  
  
2.  Dans le **Ajouter le serveur de publication** boîte de dialogue, cliquez sur **Ajouter**, puis cliquez sur **Ajouter le serveur de publication Oracle**.  
  
3.  Dans le **se connecter au serveur** boîte de dialogue, entrez le nom de la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributeur associé au serveur de publication Oracle, puis sélectionnez le type d’authentification. Si vous sélectionnez **l’authentification SQL Server**, entrez une connexion et un mot de passe. Les informations d'identification que vous spécifiez sont enregistrées par le moniteur de réplication pour se connecter à ce serveur dans le futur. Le compte Windows ou connexion SQL Server spécifiée doit être un membre de la **sysadmin** rôle serveur fixe ou un membre de la **replmonitor** rôle fixe de base de données dans la base de données de distribution.  
  
4.  Cliquez sur **Se connecter**.  
  
5.  Le nom de l’éditeur et le distributeur sont affichés dans le **Analysez l’ou les éditeurs suivant** grille.  
  
6.  Pour spécifier des options d'actualisation et de connexion pour le serveur de publication , sélectionnez le serveur de publication dans la grille et modifiez les options comme vous le souhaitez. Pour plus d’informations sur les options d’actualisation, consultez [mise en cache, l’actualisation et performances du moniteur de réplication](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
7.  Sélectionnez le groupe sous lequel le serveur de publication doit être affiché dans le moniteur de réplication. Pour créer un nouveau groupe, cliquez sur **Nouveau groupe**, puis entrez un nom de groupe ; sélectionnez le groupe dans le **Afficher cet éditeur (s) dans le groupe suivant** liste.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Pour ajouter un ou plusieurs serveurs de publication utilisant le même serveur de distribution  
  
1.  Avec le bouton droit le **le moniteur de réplication** nœud ou un éditeur de nœud dans le volet gauche de groupe, puis cliquez sur **Ajouter le serveur de publication**.  
  
2.  Dans le **Ajouter le serveur de publication** boîte de dialogue, cliquez sur **Ajouter**, puis cliquez sur **spécifier un serveur de distribution et l’ajouter ses serveurs de publication**.  
  
3.  Dans le **se connecter au serveur** boîte de dialogue, entrez le nom du serveur de distribution, puis sélectionnez le type d’authentification. Si vous sélectionnez **l’authentification SQL Server**, entrez une connexion et un mot de passe. Les informations d'identification que vous spécifiez sont enregistrées par le moniteur de réplication pour se connecter à ce serveur dans le futur. Le compte Windows ou connexion SQL Server spécifiée doit être un membre de la **sysadmin** rôle serveur fixe ou un membre de la **replmonitor** rôle fixe de base de données dans la base de données de distribution.  
  
4.  Cliquez sur **Se connecter**.  
  
5.  Le nom du serveur de distribution et de chaque serveur de publication sont affichés dans le **Analysez l’ou les éditeurs suivant** grille. Si un serveur de publication a déjà été ajouté au moniteur de réplication, il n'apparaît pas dans la grille.  
  
6.  Pour spécifier des options d'actualisation et de connexion pour le serveur de publication , sélectionnez le serveur de publication dans la grille et modifiez les options comme vous le souhaitez. Pour plus d’informations sur les options d’actualisation, consultez [mise en cache, l’actualisation et performances du moniteur de réplication](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
7.  Sélectionnez le groupe sous lequel les serveurs de publication doivent être affichés dans le moniteur de réplication. Pour créer un nouveau groupe, cliquez sur **Nouveau groupe**, puis entrez un nom de groupe ; sélectionnez le groupe dans le **Afficher cet éditeur (s) dans le groupe suivant** liste.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Pour modifier des paramètres pour le serveur de publication et pour les groupes de serveurs de publication  
  
1.  Cliquez sur un serveur de publication dans le volet gauche, puis cliquez sur **les paramètres de serveur de publication**.  
  
2.  Apportez les modifications dans le **paramètres Publisher** boîte de dialogue :  
  
    -   Pour modifier les informations d’identification que le moniteur de réplication pour se connecter à un serveur, cliquez sur **connexion éditeur** ou **connexion du serveur de distribution**, puis entrez les informations d’identification dans le **se connecter au serveur** boîte de dialogue.  
  
    -   Pour déplacer un serveur de publication d’un groupe à un autre, sélectionnez le serveur de publication dans le **Analysez l’ou les éditeurs suivant** grille, puis sélectionnez le nouveau groupe dans le **Afficher cet éditeur (s) dans le groupe suivant** liste.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Pour supprimer un serveur de publication du moniteur de réplication  
  
1.  Cliquez avec le bouton droit sur un serveur de publication dans le volet gauche.  
  
2.  Cliquez sur **Supprimer**.  
  
### Pour ajouter un groupe de serveurs de publication au moniteur de réplication  
  
1.  Les groupes de serveurs de publication peuvent être créés seulement lors de l'ajout d'un serveur de publication ou de la modification des paramètres d'un serveur de publication. Pour plus d'informations, consultez les procédures concernant l'ajout d'un serveur de publication.  
  
### Pour supprimer un groupe de serveurs de publication du moniteur de réplication  
  
1.  Déplacez tous les serveurs de publication vers un autre groupe ou supprimez-les du moniteur de réplication. Pour plus d'informations, consultez les procédures précédentes de cette rubrique.  
  
2.  Cliquez sur le groupe de serveurs de publication, puis cliquez sur **Supprimer**.  
  
## Voir aussi  
 [Configurer la distribution](../../../relational-databases/replication/configure-distribution.md)   
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  