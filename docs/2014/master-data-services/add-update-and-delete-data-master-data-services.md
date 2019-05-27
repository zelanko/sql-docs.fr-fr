---
title: Ajouter, mettre à jour et supprimer des données (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b6295ead-bd2f-49dd-8756-35c6afb59648
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 2212e7424f22ecca2619ef7215bf94b0dbb62875
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66054271"
---
# <a name="add-update-and-delete-data-master-data-services"></a>Ajouter, mettre à jour et supprimer des données (Master Data Services)
  Vous pouvez ajouter des données et apporter des modifications de données à un modèle en bloc dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
 **Conditions préalables**  
  
-   Vous devez avoir l’autorisation d’insérer des données dans la table stg.\<nom>_Leaf, the stg.\<nom>_Consolidated ou stg.\<nom>_Relationship de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
-   Vous devez avoir l’autorisation d’exécuter la procédure stockée stg.udp_\<nom>_Leaf, stg.udp\_\<nom>_Consolidated ou stg.udp\_\<nom>_Relationship dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
-   L'état du modèle ne doit pas être **Activé**.  
  
 **Pour ajouter, mettre à jour et supprimer des données dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]**  
  
1.  Préparez les membres à importer dans la table de mise en lots appropriée de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , en fournissant aussi les valeurs pour les champs obligatoires. Pour une vue d’ensemble de tables intermédiaires, consultez [importation des données &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
    -   Pour les membres feuille, la table est stg.\<nom>_Leaf, où \<nom>, fait référence à l’entité correspondante. Pour plus d’informations sur les champs requis, consultez [Table de mise en lots des membres feuille &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md).  
  
    -   Pour les membres consolidés, la table est stg.\<nom>_Consolidated. Pour plus d’informations sur les champs requis, consultez [Table de mise en lots des membres consolidés &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
    -   Pour déplacer des membres dans les hiérarchies explicites, la table est stg.\<nom>_Relationship. Pour plus d’informations sur les champs requis, consultez [Table de mise en lots des relations &#40;Master Data Services&#41;](../../2014/master-data-services/relationship-staging-table-master-data-services.md).  
  
         Pour une vue d’ensemble sur le déplacement de membres dans les hiérarchies explicites, consultez [importation des données &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
    -   Utilisez la valeur du champ **ImportType** pour spécifier que vous créez des membres, que vous désactivez des membres ou que vous supprimez des membres. Pour plus d’informations sur les valeurs, consultez [Table de mise en lots des membres feuille &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md) et [Table de mise en lots des membres consolidés &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
         Pour une vue d’ensemble de la désactivation et suppression de membres, consultez [importation des données &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
2.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l'instance du moteur de base de données pour votre base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
     Pour plus d'informations, consultez [SQL Server Management Studio](../ssms/sql-server-management-studio-ssms.md).  
  
3.  Importez les données dans les tables de mise en lots à l'aide de l'Assistant Importation et exportation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
     Pour plus d'informations, consultez [Assistant Importation et Exportation SQL Server](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
4.  Chargez les données depuis les tables de mise en lots dans les tables [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , en effectuant une des opérations suivantes :  
  
    -   Exécutez la procédure stockée de mise en lots qui correspond à la table de mise en lots vers laquelle vous voulez déplacer des données.  
  
         Pour une vue d’ensemble de procédures stockées de mise en lots et d’organiser les tables, consultez [importation des données &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md). Pour plus d’informations sur les paramètres des procédures stockées de mise en lots et un exemple de code, consultez [Procédure stockée de mise en lots &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).  
  
    -   Utilisez la zone de la fonction **Gestion de l'intégration** de la gestion des données de référence.  
  
         Dans la page **Lots intermédiaires** , sélectionnez le modèle auquel vous ajoutez des données dans la liste déroulante, puis cliquez sur **Démarrer les lots**. L'état du traitement par lots est indiqué dans le champ **État** . Pour plus d’informations sur les états, consultez [États d’importation &#40;Master Data Services&#41;](../../2014/master-data-services/import-statuses-master-data-services.md).  
  
         ![Page Lots intermédiaires dans Master Data Manager](../../2014/master-data-services/media/mds-staging-batches.png "Page Lots intermédiaires dans Master Data Manager")  
  
         Le processus de site est démarré à des intervalles déterminés par le paramètre **Intervalle de lot intermédiaire** dans [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Pour plus d’informations, consultez [Paramètres système &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
5.  Afficher les erreurs rencontrées lors de la mise en lots. Pour plus d’informations, consultez [afficher les erreurs qui se produisent pendant le processus de mise en lots &#40;Master Data Services&#41; ](view-errors-that-occur-during-staging-master-data-services.md) et [erreurs du processus de mise en lots &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
6.  Validation de données par rapport aux règles d'entreprise  
  
     Dans Master Data Manager, accédez à la zone de la fonction **Explorer** pour votre modèle, puis appliquez des règles d'entreprise pour valider les données. Pour plus d’informations, consultez [Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md). Vous pouvez également utiliser une procédure stockée pour valider les données. Pour plus d’informations, consultez [Procédure stockée de validation &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
     Quand vous chargez des données à partir des tables de mise en lots, elles ne sont pas validées automatiquement par rapport aux règles d'entreprise. Pour plus d’informations sur la validation et quand elle a lieu, consultez [Validation &#40;Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Importation de données &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
  
