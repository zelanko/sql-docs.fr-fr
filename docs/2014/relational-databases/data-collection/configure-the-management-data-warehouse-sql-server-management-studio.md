---
title: Configurer l’entrepôt de données de gestion (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollection.wizard_finish.f1
- sql12.swb.dc.datacollection.wizard_maploginuser.f1
- sql12.swb.dc.datacollection.wizard_welcome.f1
- sql12.swb.dc.datacollection.wizard_choosemdw.f1
- sql12.swb.dc.datacollection.wizard_completecfg.f1
- sql12.swb.dc.datacollection.wizard_config.f1
- sql12.swb.dc.datacollection.wizard_createmdw.f1
helpviewer_keywords:
- data warehouse [SQL Server], multiple instances
- data warehouse [SQL Server], configuring
- Configure Management Data Warehouse Wizard
- management data warehouse, configuring
ms.assetid: 23a584f3-c5e1-414c-9afe-73cd7efbda4b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a29a8b9adda07015a7f6fec953db42748a1e752e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62918818"
---
# <a name="configure-the-management-data-warehouse-sql-server-management-studio"></a>Configurer l'entrepôt de données de gestion (SQL Server Management Studio)
  Cette rubrique explique comment configurer l'entrepôt de données de gestion pour prendre en charge le stockage des données sur une instance unique ou plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui utilisent le collecteur de données. Ces instances peuvent se trouver sur le même serveur ou sur différents serveurs. Cette rubrique fournit également des descriptions de l'interface utilisateur pour la boîte de dialogue [Assistant Configuration de l'entrepôt de gestion des données](#Wizard) . Pour plus d'informations sur la configuration d'un collecteur de données, consultez [Configure Properties of a Data Collector](configure-properties-of-a-data-collector.md).  
  
> [!NOTE]  
>  Si l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour s'exécuter à l'aide de l'un des comptes de service système (système local, service réseau ou service local) et que l'entrepôt de données de gestion est créé sur une instance différente du collecteur de données, vous devez configurer les jeux d'éléments de collecte de sorte qu'ils utilisent un proxy pour télécharger les données vers l'entrepôt de données de gestion.  
  
### <a name="configure-the-management-data-warehouse-on-a-single-instance-or-multiple-instances-of-ssnoversion"></a>Configurer l'entrepôt de données de gestion sur une instance unique ou plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  Vérifiez que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute.  
  
2.  Dans l'Explorateur d'objets, développez le nœud **Gestion** .  
  
3.  Cliquez avec le bouton droit sur **Collecte de données**, développez **Tâches**, puis cliquez sur **Configurer l’entrepôt de données de gestion**.  
  
4.  Utilisez l' [Assistant Configuration de l'entrepôt de données de gestion](#Wizard) pour créer un entrepôt de données de gestion, configurer des connexions, activer la collecte de données et démarrer les **jeux d'éléments de collecte de données système**.  
  
     Pour configurer plusieurs instances, passez à l'étape 5.  
  
    > [!NOTE]  
    >  L'utilisation de proxys dans les déploiements où le collecteur de données est installé sur plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui utilisent le même entrepôt de données de gestion est considérée comme étant la meilleure pratique.  
  
5.  Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sur une autre instance et procédez de l'une des manières suivantes :  
  
    -   Utilisez l'Assistant Configuration de l'entrepôt de données de gestion pour configurer la collecte de données pour l'entrepôt de données de gestion existant.  
  
    -   Cliquez avec le bouton droit sur **Collecte de données**, puis cliquez sur **Propriétés**. Sous l'onglet **Général** , spécifiez l'entrepôt de données de gestion existant et le serveur sur lequel il est installé.  
  
6.  Répétez l'étape 5 jusqu'à ce que toutes les instances de base de données qui utilisent le collecteur de données soient configurées pour télécharger les données vers l'entrepôt de données de gestion partagé.  
  
####  <a name="configure-management-data-warehouse-wizard"></a><a name="Wizard"></a> Assistant Configuration de l'entrepôt de données de gestion  
 **Page d'accueil**  
  
 La page d'accueil est la page de démarrage de l'Assistant Configuration de la collecte de données. L'affichage de cette page est facultatif.  
  
 **Ne plus afficher cette page de démarrage.**  
 Sélectionnez cette option pour supprimer cette page la prochaine fois vous lancez l'Assistant Configuration de la collecte de données.  
  
 **Page Configuration du stockage de l'entrepôt de données de gestion**  
  
 Utilisez cette page pour sélectionner un serveur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un entrepôt de données de gestion. L'entrepôt de données de gestion est une base de données relationnelle qui sert de stockage pour les données collectées.  
  
> [!NOTE]  
>  Vous devez disposer du niveau d'autorisations approprié pour créer l'entrepôt de données de gestion sur le serveur. Pour plus d’informations, consultez [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql). Vous devez également disposer du niveau d'autorisations approprié pour créer des connexions pour les rôles d'entrepôt de données de gestion.  
  
 **Nom du serveur**  
 Spécifie le nom du serveur qui hébergera l'entrepôt de données de gestion.  
  
 Lors de la configuration d'un entrepôt de données de gestion, **Nom du serveur** est toujours le nom du serveur local et ne peut pas être modifié.  
  
 **Nom de la base de données**  
 Spécifie la base de données relationnelle qui stockera les données collectées. Utilisez la liste pour sélectionner une base de données existante ou cliquez sur **Nouveau** pour créer une base de données à l'aide de la boîte de dialogue **Nouvelle base de données** .  
  
 L'option **Nouveau** est disponible uniquement lors de la configuration d'un jeu d'éléments de collecte de données.  
  
 **Page Mapper les connexions et les utilisateurs**  
  
 Utilisez cette page pour mapper des connexions à des rôles d'utilisateur de base de données pour l'entrepôt de données de gestion.  
  
 **Utilisateurs mappés à cette connexion**  
 Affiche les connexions existantes sur le serveur qui hébergera l'entrepôt de données de gestion. Chaque ligne contient une case à cocher **Mappage** modifiable, un nom de **Connexion** et un **Type** de connexion.  
  
 Spécifiez une connexion en activant la case à cocher **Mappage** pour la connexion.  
  
 **Appartenance au rôle de base de données pour :**  *\<nom_entrepôt_données>*  
 Sélectionnez le rôle d'entrepôt de données de gestion auquel la connexion est mappée en cliquant sur une ou plusieurs cases à cocher en regard des options suivantes :  
  
-   **mdw_admin**  
  
-   **mdw_reader**  
  
-   **mdw_writer**  
  
 **Nouvelle connexion**  
 Ouvrez la boîte de dialogue **Nouvelle connexion** et créez une connexion pour l’entrepôt de données de gestion.  
  
 **Page Fin de l'Assistant**  
  
 Utilisez cette page pour vérifier et terminer la configuration de la collecte de données. L'arborescence contenue dans la fenêtre d'affichage indique les configurations qui s'appliquent ainsi que les actions qui sont entreprises lorsque vous cliquez sur **Terminer**.  
  
 **Page Progression de l'Assistant Configuration de la collecte de données**  
  
 Utilisez cette page pour consulter les résultats de chaque étape de configuration.  
  
 **Détails**  
 Affiche chaque étape de configuration sous la forme d’une ligne dans la grille **Détails** . Chaque ligne contient une colonne **Action** qui décrit l'étape et une colonne **État** qui indique la réussite ou l'échec de l'étape. En cas d'erreur, un message s'affiche dans la colonne **Message** .  
  
 **Stop**  
 Arrête le traitement de l'Assistant.  
  
 **Report**  
 Affiche un rapport de la configuration de la collecte de données. Les options de rapport suivantes sont fournies :  
  
-   Afficher le rapport  
  
-   Enregistrer le rapport dans un fichier  
  
-   Copier le rapport dans le Presse-papiers  
  
-   Envoyer le rapport sous forme de courrier électronique  
  
 **Close**  
 Ferme l'Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_syscollector_enable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql)   
 [sp_syscollector_disable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql)   
 [Collecte de données](data-collection.md)   
 [Gérer la collecte de données](manage-data-collection.md)  
  
  
