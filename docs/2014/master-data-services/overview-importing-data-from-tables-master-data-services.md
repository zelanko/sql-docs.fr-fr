---
title: Importation de données (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], about staging process
- importing data [Master Data Services]
- staging process [Master Data Services]
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3d1ad35a40e4218bfef44daeec01ee03fc0c7c78
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175984"
---
# <a name="data-import-master-data-services"></a>Importation de données (Master Data Services)
  Une fois que vous avez créé un modèle pour vos données dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez commencer à ajouter des données et à apporter des modifications aux données de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .   Vous utilisez les tables de mise en lots [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , les procédures stockées et Master Data Manager.

 Vous pouvez également utiliser le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]pour ajouter des données au référentiel MDS ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] base de données). Pour plus d’informations, consultez [publication de données &#40;Complément MDS pour Excel&#41;](microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).

 Lorsque vous ajoutez et mettez à jour des données, procédez comme suit.

-   Charger et mettre à jour les membres, puis mettre à jour les valeurs d'attribut

-   Désactiver et supprimer les membres

-   Déplacer les membres d’une hiérarchie explicite

 L’ajout et la mise à jour des données incluent les tâches principales suivantes.

1.  Chargez les données dans des tables de mise en lots dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .

2.  Chargez les données des tables de mise en lots vers les tables [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] appropriées.

     Vous utilisez des procédures stockées intermédiaires ou [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour charger les données.

> [!NOTE]
>  Dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], la prise en charge des processus de mise en lots [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] est déconseillée.

## <a name="deactivating-and-deleting-members"></a>Désactivation et suppression de membres
 La désactivation signifie que le membre peut être réactivé. La réactivation d'un membre permet de restaurer ses attributs et son appartenance aux hiérarchies et collections. Toutes les transactions précédentes sont intactes. Les transactions de désactivation sont visibles par les administrateurs dans la zone fonctionnelle **Gestion des versions** de Master Data Manager.

 La suppression signifie retirer définitivement le membre du système. Toutes les transactions du membre, toutes les relations et tous les attributs sont supprimés définitivement.

> [!NOTE]
>  Vous ne pouvez pas utiliser la mise en lots pour réactiver des membres. Vous devez le faire manuellement dans Master Data Manager. Pour plus d’informations, consultez [Réactiver un membre ou une collection &#40;Master Data Services&#41;](reactivate-a-member-or-collection-master-data-services.md).
> 
>  Vous ne pouvez pas utiliser la mise en lots pour supprimer ou désactiver des collections. Pour plus d’informations sur la désactivation manuelle des collections, consultez [Supprimer un membre ou une collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md).

## <a name="moving-explicit-hierarchy-members"></a>Déplacement des membres d’une hiérarchie explicite
 Lorsque vous déplacez en bloc des membres des hiérarchies explicites, vous pouvez désigner les membres comme suit.

-   Un membre consolidé comme un parent d'un membre consolidé.

-   Un membre consolidé comme un parent d'un membre feuille.

-   Un membre feuille comme un frère d'une feuille ou un membre consolidé.

-   Un membre consolidé comme un frère d'une feuille ou un membre consolidé.

## <a name="staging-tables-and-stored-procedures"></a>Tables de mise en lots et procédures stockées
 La base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] inclut les types suivants de tables de mise en lots que vous pouvez remplir avec vos données.

-   [Table de mise en lots des membres feuille &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)

-   [Table de mise en lots des membres consolidés &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)

-   [Table de mise en lots des relations &#40;Master Data Services&#41;](../../2014/master-data-services/relationship-staging-table-master-data-services.md)

 Pour chaque entité du modèle, il existe une table de mise en lots. Le nom de la table indique l'entité correspondante et le type d'entité comme membre feuille. L'illustration suivante montre les tables de mise en lots pour les entités Devise, Client et Produit.

 ![Tables intermédiaires dans la base de données MDS](../../2014/master-data-services/media/mds-stagingtables.png "Tables intermédiaires dans la base de données MDS")

 Le nom de la table est spécifié lors de la création d'une entité et ne peut pas être modifié. Si le nom de la table de mise en lots contient un _1 ou tout autre nombre, une autre table de ce nom existait déjà lorsque l'entité a été créée.

 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] inclut les types suivants de procédures stockées de mise en lots.

-   stg.udp_\<nom>_Leaf

-   stg.udp_\<nom>_Consolidated

-   stg.udp_\<nom>_Relationship

 Pour chaque entité du modèle, il existe trois procédures stockées qui correspondent à un membre feuille, un membre consolidé et les tables de mise en lots de relations.  L'illustration suivante montre les procédures stockées de mise en lots pour les entités Devise, Client et Produit.

 ![Procédures stockées intermédiaires dans la base de données MDS](../../2014/master-data-services/media/mds-stagingstoredprocedures.png "Procédures stockées intermédiaires dans la base de données MDS")

 Pour plus d’informations sur les procédures stockées, consultez [Procédure stockée de mise en lots &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).

## <a name="logging-transactions"></a>Journalisation des transactions
 Toutes les transactions qui se produisent lors de l'importation ou de la mise à jour des données ou des relations peuvent être enregistrées dans un journal. Une option dans la procédure stockée permet cette journalisation. Si vous initialisez le processus de site à l’aide de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], aucune journalisation n'a lieu.

 Dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], le paramètre **Journaliser toutes les transactions intermédiaires** ne s'applique pas à cette méthode de mise en lot des données.

## <a name="related-content"></a>Contenu associé

-   [Validation &#40;Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md)

-   [Règles d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)


