---
title: Déployer des stratégies planifiées sur plusieurs instances | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0d3f2412114e50292c91908b3a20c433d022b239
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057607"
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
  
-   Les serveurs sur lesquels vous souhaitez déployer les stratégies planifiées doivent être enregistrés dans les serveurs inscrits dans le nœud groupes de serveurs **locaux** ou **serveurs de gestion centralisée** . Pour plus d'informations, voir les rubriques suivantes :  
  
    -   [Créer ou modifier un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   [Inscrire un serveur connecté &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).  
  
    -   [Créer un serveur d’administration centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a>Pour exporter les stratégies planifiées sous la forme de fichiers .xml  
  
1.  Sur le serveur où vous avez configuré les stratégies planifiées au cours de la tâche précédente, développez **gestion**, gestion de la **stratégie**, puis cliquez sur **stratégies**.  
  
2.  Dans le menu **Affichage** , cliquez sur **Détails de l’Explorateur d’objets**.  
  
3.  Dans le volet Détails de l' **Explorateur d’objets** , sélectionnez toutes les stratégies des meilleures pratiques planifiées que vous souhaitez déployer sur d’autres serveurs via les serveurs inscrits.  
  
    > [!NOTE]  
    >  Vous pouvez cliquer sur l’en-tête **catégorie** pour trier les stratégies par catégorie.  
  
4.  Cliquez avec le bouton droit sur la sélection, puis cliquez sur **Exporter la stratégie**.  
  
5.  Si vous avez sélectionné plusieurs stratégies à exporter, dans la boîte de dialogue **Rechercher un dossier** , sélectionnez un dossier de destination ou créez un nouveau dossier. Pour cette leçon, créez un nouveau dossier avec le chemin **c:\ Scheduled_BP_Policies**, puis cliquez sur **OK**.  
  
     Si vous avez sélectionné une seule stratégie à exporter, dans la boîte de dialogue **Exporter la stratégie** , créez un nouveau dossier avec le chemin **c:\ Scheduled_BP_Policies**, cliquez sur **ouvrir**, puis sur **Enregistrer**.  
  
     Les fichiers de stratégie .xml sont créés à l'emplacement du dossier.  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a>Pour déployer les stratégies planifiées sur des serveurs qui sont gérés via les serveurs inscrits  
  
1.  Dans le menu **Affichage** , cliquez sur **Serveurs inscrits**.  
  
2.  Développez **moteur de base de données**, développez **groupes de serveurs locaux** ou **serveurs de gestion centralisée**, cliquez avec le bouton droit sur le nœud sur lequel vous souhaitez déployer les stratégies, puis cliquez sur **importer des stratégies**.  
  
    > [!NOTE]  
    >  Si vous cliquez avec le bouton droit sur **groupes de serveurs locaux** ou sur le serveur de gestion centralisée, les stratégies sont déployées sur tous les serveurs gérés. Si vous cliquez avec le bouton droit sur un groupe de serveurs spécifique, les stratégies seront déployées uniquement sur les serveurs de ce groupe. Si vous cliquez avec le bouton droit sur un serveur inscrit spécifique, les stratégies seront déployées uniquement sur ce serveur.  
  
3.  En regard de **fichiers à importer**, cliquez sur le bouton de sélection (**...**).  
  
4.  Dans la boîte de dialogue **Sélectionner une stratégie** , accédez à l’emplacement du dossier où vous avez enregistré les stratégies planifiées. Pour cet exemple, accédez à l’emplacement **c:\ Scheduled_BP_Policies**.  
  
5.  Sélectionnez les stratégies que vous souhaitez importer dans les instances cibles, puis cliquez sur **ouvrir**.  
  
6.  Dans la boîte de dialogue **Importer** , dans la liste État de la **stratégie** , sélectionnez l’état de stratégie souhaité. Vous pouvez choisir de conserver l'état de la stratégie, d'activer les stratégies ou de les désactiver lors de l'importation. Sachez que les stratégies doivent être activées pour s'exécuter selon une planification.  
  
7.  Cliquez sur **OK** pour importer les stratégies vers toutes les instances cibles.  
  
    > [!NOTE]  
    >  En cas d’erreur, la boîte de dialogue **Importer** ne disparaît pas. Cliquez sur la page **Journal** pour passer en revue les messages. Cliquez sur **Annuler** pour refermer la boîte de dialogue.  
  
8.  Pour afficher les stratégies à partir d’une instance cible, connectez-vous à l’instance, ouvrez l’Explorateur d’objets, développez **gestion**, puis développez **stratégies**. Vous devez voir les stratégies importées dans le nœud **stratégies** . Si vous double-cliquez sur chaque stratégie, vous pouvez afficher la planification ou modifier les paramètres.  
  
    > [!NOTE]  
    >  Pour afficher les résultats d'évaluation après l'exécution d'une stratégie planifiée, ouvrez le journal Historique de la stratégie sur l'instance cible. Pour ouvrir le journal, cliquez avec le bouton droit sur **gestion des stratégies**, puis cliquez sur **afficher l’historique**.  
  
## <a name="summary"></a>Résumé  
 Ce didacticiel vous a montré comment effectuer des évaluations à la demande et des évaluations planifiées des stratégies des meilleures pratiques sur une ou plusieurs instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="next"></a>Suivant  
 Ce didacticiel est terminé. Pour revenir au début, consultez [Didacticiel : évaluation des meilleures pratiques à l’aide de la gestion basée sur des stratégies](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md).  
  
 Pour afficher la liste des [!INCLUDE[ssDE](../includes/ssde-md.md)] didacticiels, cliquez sur [moteur de base de données didacticiels](../relational-databases/database-engine-tutorials.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
