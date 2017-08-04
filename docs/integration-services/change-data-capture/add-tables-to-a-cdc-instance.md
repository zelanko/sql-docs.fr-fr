---
title: "Ajouter des Tables à une Instance de capture de données modifiées | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- addTabs
ms.assetid: ad260e19-c021-4035-9311-c02fc96ceaea
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ee8cd785cdb0facdba880ee0502ec51508bca618
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="add-tables-to-a-cdc-instance"></a>Ajouter des tables à une instance de capture de données modifiées
  Utilisez la boîte de dialogue Sélection de table pour ajouter des tables supplémentaires de la source Oracle à l'instance de capture de données modifiées. Les tables sélectionnées sont ajoutées à la liste sous l'onglet **Tables** de l'éditeur de propriétés.  
  
 Par défaut, aucune table n'est incluse dans la liste des tables de cette boîte de dialogue. Vous pouvez cocher la case **(Sélectionner tout)** ou rechercher des tables spécifiques.  
  
 **Pour rechercher des tables spécifiques**  
 Entrez les critères de recherche comme suit, puis cliquez sur **Rechercher**:  
  
-   **Schéma**: dans la liste, sélectionnez un schéma de base de données. Seules les tables qui ont ce schéma seront incluses dans la liste.  
  
-   **Modèle de nom de table**: entrez n'importe quelle chaîne de caractères. Seules les tables qui incluent la chaîne de caractères entrée s'affichent.  
  
> [!NOTE]  
>  Vous pouvez entrer des critères dans un des deux champs ou dans les deux.  
  
-   **Afficher les 1 000 premières tables correspondantes**: par défaut cette case à cocher est activée. Elle limite l'affichage aux 1 000 premières tables correspondantes. Si vous désactivez la case à cocher, toutes les tables qui correspondent aux critères s'affichent. S'il existe un grand nombre de tables, l'affichage de la liste peut prendre beaucoup de temps.  
  
 **Pour sélectionner les tables à inclure dans l'instance CDC**  
 Cochez la case en regard d’une table à inclure, puis cliquez sur **Ajouter**. Les tables sont ajoutées à la liste dans la page **Sélectionner des tables et des colonnes** de l'Assistant Nouvelle instance.  
  
 Cliquez sur **Fermer** pour fermer la boîte de dialogue sans ajouter de table.  
  
> [!NOTE]  
>  Si vous sélectionnez une table qui inclut un type de données non pris en charge, un message d'erreur s'affiche et la table n'est pas incluse.  
  
> [!NOTE]  
>  Vous pouvez afficher la liste des tables dans la visionneuse. Lorsque vous utilisez la visionneuse, les informations sont en lecture seule. La visionneuse inclut également la liste des colonnes capturées dans la table. Pour plus d'informations sur l'accès à la visionneuse, consultez [How to Manage a CDC Instance](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment modifier les propriétés d’Instance de capture de données modifiées](../../integration-services/change-data-capture/how-to-edit-the-cdc-instance-properties.md)   
 [Comment gérer une Instance de capture de données modifiées](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [Sélectionner des Tables Oracle pour capturer les modifications](../../integration-services/change-data-capture/select-oracle-tables-for-capturing-changes.md)  
  
  
