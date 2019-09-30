---
title: Ajouter des tables à une instance CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- addTabs
ms.assetid: ad260e19-c021-4035-9311-c02fc96ceaea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa9bf38512b2ba817156f216161d21bc1d27c129
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71294860"
---
# <a name="add-tables-to-a-cdc-instance"></a>Ajouter des tables à une instance de capture de données modifiées

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Utilisez la boîte de dialogue Sélection de table pour ajouter des tables supplémentaires de la source Oracle à l'instance de capture de données modifiées. Les tables sélectionnées sont ajoutées à la liste sous l'onglet **Tables** de l'éditeur de propriétés.  
  
 Par défaut, aucune table n'est incluse dans la liste des tables de cette boîte de dialogue. Vous pouvez cocher la case **(Sélectionner tout)** ou rechercher des tables spécifiques.  
  
 **Pour rechercher des tables spécifiques**  
 Entrez les critères de recherche comme suit, puis cliquez sur **Rechercher**:  
  
-   **Schéma** : sélectionnez un schéma de base de données dans la liste. Seules les tables qui ont ce schéma seront incluses dans la liste.  
  
-   **Modèle de nom de table** : entrez une chaîne de caractères. Seules les tables qui incluent la chaîne de caractères entrée s'affichent.  
  
> [!NOTE]  
>  Vous pouvez entrer des critères dans un des deux champs ou dans les deux.  
  
-   **Afficher les 1 000 premières tables correspondantes** : cette case est cochée par défaut. Elle limite l'affichage aux 1 000 premières tables correspondantes. Si vous désactivez la case à cocher, toutes les tables qui correspondent aux critères s'affichent. S'il existe un grand nombre de tables, l'affichage de la liste peut prendre beaucoup de temps.  
  
 **Pour sélectionner les tables à inclure dans l'instance CDC**  
 Cochez la case en regard d’une table à inclure, puis cliquez sur **Ajouter**. Les tables sont ajoutées à la liste dans la page **Sélectionner des tables et des colonnes** de l'Assistant Nouvelle instance.  
  
 Cliquez sur **Fermer** pour fermer la boîte de dialogue sans ajouter de table.  
  
> [!NOTE]  
>  Si vous sélectionnez une table qui inclut un type de données non pris en charge, un message d'erreur s'affiche et la table n'est pas incluse.  
  
> [!NOTE]  
>  Vous pouvez afficher la liste des tables dans la visionneuse. Lorsque vous utilisez la visionneuse, les informations sont en lecture seule. La visionneuse inclut également la liste des colonnes capturées dans la table. Pour plus d'informations sur l'accès à la visionneuse, consultez [How to Manage a CDC Instance](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : modifier les propriétés d'une instance de capture de données modifiées](../../integration-services/change-data-capture/how-to-edit-the-cdc-instance-properties.md)   
 [How to Manage a CDC Instance](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [Sélectionner des tables Oracle pour capturer des modifications](../../integration-services/change-data-capture/select-oracle-tables-for-capturing-changes.md)  
  
  
