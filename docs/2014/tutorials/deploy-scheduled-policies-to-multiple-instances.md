---
title: Déployer des stratégies planifiées vers plusieurs Instances | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
caps.latest.revision: 6
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ebabe1d982f427002eea31f09541cd40654bcfc1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249529"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a>Déployer des stratégies planifiées sur plusieurs instances
  En utilisant des serveurs inscrits, vous pouvez déployer des stratégies planifiées sur des serveurs gérés à partir d'un emplacement central. Vous pouvez déployer des stratégies planifiées à partir d'un groupe de serveurs locaux ou à partir d'un serveur de gestion centralisée.  
  
 Dans cette tâche, vous effectuerez les opérations suivantes :  
  
1.  exporter vers un dossier les stratégies que vous avez planifiées au cours de la tâche précédente ;  
  
2.  déployer les stratégies planifiées sur des instances cibles qui sont gérées via les serveurs inscrits.  
  
 Vous effectuerez ces tâches sur l'ordinateur sur lequel vous avez effectué la tâche précédente de cette leçon.  
  
## <a name="prerequisites"></a>Prérequis  
 Les conditions préalables de cette tâche sont les suivantes :  
  
-   Vous devez avoir effectué les tâches précédentes de cette leçon.  
  
-   Les instances sur lesquelles vous voulez déployer les stratégies planifiées doivent exécuter [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ou version ultérieure. L'automation requiert que les stratégies soient stockées localement, ce qui n'est pas pris en charge sur les versions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
-   Les serveurs où vous souhaitez déployer les stratégies planifiées doivent être inscrits dans serveurs inscrits dans le le **groupes de serveurs locaux** ou **des serveurs d’administration centrale** nœud. Pour plus d'informations, consultez les rubriques suivantes :  
  
    -   [Créer ou modifier un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   [Inscrire un serveur connecté &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
    -   [Créer un serveur d’administration centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a>Pour exporter les stratégies planifiées sous la forme de fichiers .xml  
  
1.  Sur le serveur où vous avez configuré des stratégies planifiées dans la tâche précédente, développez **gestion**, développez **gestion des stratégies de**, puis cliquez sur **stratégies**.  
  
2.  Dans le menu **Affichage** , cliquez sur **Détails de l’Explorateur d’objets**.  
  
3.  Dans le **détails de l’Explorateur d’objets** volet, sélectionnez toutes les meilleures pratiques planifiées des stratégies que vous souhaitez déployer sur d’autres serveurs via des serveurs inscrits.  
  
    > [!NOTE]  
    >  Vous pouvez cliquer sur le **catégorie** titre pour trier les stratégies par catégorie.  
  
4.  Avec le bouton droit de la sélection, puis cliquez sur **exporter la stratégie**.  
  
5.  Si vous avez sélectionné plusieurs stratégies à exporter, dans le **rechercher un dossier** boîte de dialogue, sélectionnez un dossier de destination, ou créez un dossier. Pour cette leçon, créez un dossier avec le chemin d’accès **C:\Scheduled_BP_Policies**, puis cliquez sur **OK**.  
  
     Si vous n’avez sélectionné une stratégie à exporter, dans le **exporter la stratégie** boîte de dialogue zone, créez un nouveau dossier ayant le chemin d’accès **C:\Scheduled_BP_Policies**, cliquez sur **Open**, puis cliquez sur **Enregistrer**.  
  
     Les fichiers de stratégie .xml sont créés à l'emplacement du dossier.  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a>Pour déployer les stratégies planifiées sur des serveurs qui sont gérés via les serveurs inscrits  
  
1.  Dans le menu **Affichage** , cliquez sur **Serveurs inscrits**.  
  
2.  Développez **moteur de base de données**, développez le **groupes de serveurs locaux** ou **des serveurs d’administration centrale**, cliquez sur le nœud que vous souhaitez déployer les stratégies, puis Cliquez sur **importer des stratégies**.  
  
    > [!NOTE]  
    >  Si vous cliquez sur **groupes de serveurs locaux** ou le serveur de gestion centralisée lui-même, les stratégies seront déployées pour tous les serveurs gérés. Si vous cliquez avec le bouton droit sur un groupe de serveurs spécifique, les stratégies seront déployées uniquement sur les serveurs de ce groupe. Si vous cliquez avec le bouton droit sur un serveur inscrit spécifique, les stratégies seront déployées uniquement sur ce serveur.  
  
3.  Regard **fichiers à importer**, cliquez sur le bouton de sélection (**...** ).  
  
4.  Dans le **sélectionner la stratégie** boîte de dialogue, accédez à l’emplacement du dossier où vous avez enregistré les stratégies planifiées. Pour cet exemple, accédez à l’emplacement **C:\Scheduled_BP_Policies**.  
  
5.  Sélectionnez les stratégies que vous souhaitez importer dans les instances cibles, puis cliquez sur **Open**.  
  
6.  Dans le **importation** boîte de dialogue le **état de la stratégie** liste, sélectionnez l’état de la stratégie de votre choix. Vous pouvez choisir de conserver l'état de la stratégie, d'activer les stratégies ou de les désactiver lors de l'importation. Sachez que les stratégies doivent être activées pour s'exécuter selon une planification.  
  
7.  Cliquez sur **OK** pour importer les stratégies dans toutes les instances cibles.  
  
    > [!NOTE]  
    >  S’il existe des erreurs, le **importation** boîte de dialogue ne disparaît pas. Cliquez sur le **journal** page pour consulter les messages. Cliquez sur **Annuler** pour fermer la boîte de dialogue.  
  
8.  Pour afficher les stratégies à partir d’une instance cible, connectez-vous à l’instance, ouvrez l’Explorateur d’objets, développez **gestion**, puis développez **stratégies**. Vous devez voir les stratégies importées dans le **stratégies** nœud. Si vous double-cliquez sur chaque stratégie, vous pouvez afficher la planification ou modifier les paramètres.  
  
    > [!NOTE]  
    >  Pour afficher les résultats d'évaluation après l'exécution d'une stratégie planifiée, ouvrez le journal Historique de la stratégie sur l'instance cible. Pour ouvrir le journal, avec le bouton droit **gestion des stratégies de**, puis cliquez sur **afficher l’historique**.  
  
## <a name="summary"></a>Résumé  
 Ce didacticiel vous a montré comment effectuer des évaluations à la demande et des évaluations planifiées des stratégies des meilleures pratiques sur une ou plusieurs instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="next"></a>Suivant  
 Ce didacticiel est terminé. Pour revenir au début, consultez [didacticiel : évaluation des meilleures pratiques par la gestion basée sur des](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md).  
  
 Pour afficher la liste de [!INCLUDE[ssDE](../includes/ssde-md.md)] didacticiels, cliquez sur [didacticiels sur le moteur de base de données](../relational-databases/database-engine-tutorials.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
