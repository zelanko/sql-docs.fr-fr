---
title: "Apporter des modifications aux tables sélectionnées pour capturer les modifications | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d6df6c0e20cb81a1525998da5934637d6ad6c29
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a>Apporter des modifications aux tables sélectionnées pour capturer les modifications
  Cette boîte de dialogue, vous permet de sélectionner des colonnes spécifiques de la table sélectionnée pour la capture des modifications. Vous pouvez également modifier les informations du **Rôle de sécurité** et de l' **Instance de capture** .  
  
 Vous pouvez apporter les modifications suivantes aux tables sélectionnées pour capturer les modifications dans cette boîte de dialogue.  
  
 **Apporter des modifications aux colonnes incluses dans l'instance de capture de données modifiées :**  
  
 Effectuez une des actions suivantes ou les deux :  
  
-   Activez la case à cocher en regard des colonnes supplémentaires à inclure.  
  
-   Désactivez la case à cocher en regard des colonnes que vous ne souhaitez plus inclure.  
  
 **Modifier le type de données d'une colonne spécifique**:  
  
 Vous pouvez sélectionner un type de données différent pour une colonne spécifique. Vous ne pouvez remplacer le type de données que par un type de données compatible avec le type de données d'origine.  
  
 Pour changer de type de données, cliquez dans la colonne **Type de données** , puis sélectionnez un autre type de données. Seuls les types de données compatibles avec le type de données d'origine sont disponibles.  
  
> [!NOTE]  
>  Si aucun type de données supplémentaire ne peut être sélectionné, la liste déroulante n'est pas disponible.  
  
 **Modifier le rôle de sécurité**  
  
 Tapez un nouveau nom ou modifiez le rôle de régulation de la sécurité dans le champ **Rôle de sécurité** .  
  
 **Modifier ou ajouter une instance de capture**  
  
 Dans le champ **Instance de capture** , entrez un nom pour l'instance de capture.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : créer l'instance SQL Server de base de données de modifications](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Sélectionner des tables et des colonnes Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  
