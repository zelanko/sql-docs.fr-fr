---
title: Modifier des Tables | Documents Microsoft
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
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: aece26acf5992160124dfa14eda26a524e82ff5a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="edit-tables"></a>Modifier des tables
  Utilisez l'onglet **Tables** pour apporter des modifications aux tables et aux colonnes sélectionnées dans la base de données source Oracle. Cet onglet contient les éléments suivants :  
  
 **Liste Table**  
 La liste de tables comporte trois colonnes :  
  
-   **Nom de la table Oracle**: nom de la table, y compris du schéma de la table.  
  
-   **Instance de capture**: nom de l’instance de capture utilisée pour nommer les objets de capture de données modifiées spécifiques à l’instance. L'instance de capture ne peut pas être NULL. S'il n'est pas spécifié, le nom est dérivé du nom de schéma d'origine associé au nom de table source au format `<schema-name>_<table-name>.` . Le nom de l'instance de capture ne peut pas dépasser 100 caractères et doit être unique dans la base de données. Vous pouvez cliquer dans n’importe quelle cellule de cette colonne pour modifier manuellement **capture_instance**.  
  
-   **Rôle de sécurité**: nom du rôle de base de données utilisé pour obtenir l'accès aux données modifiées. Vous pouvez cliquer dans n’importe quelle cellule de cette colonne pour modifier manuellement **security_role**.  
  
 **Ajouter des tables**  
 Cliquez sur **Ajouter des tables** pour ouvrir la boîte de dialogue Sélection de table dans laquelle vous pouvez [ajouter des tables à une instance de capture de données modifiées](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md). Lorsque vous accédez pour la première fois à la base de données Oracle, vous devez [Connect to Oracle](../../integration-services/change-data-capture/connect-to-oracle.md).  
  
 **Modifier**  
 Sélectionnez une table dans la liste et cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Propriétés** de cette table dans laquelle vous pouvez [Modifier les propriétés d’une table](../../integration-services/change-data-capture/edit-the-table-properties.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas modifier le mappage de type pour les tables qui possèdent déjà des tables miroir. Vous ne pouvez le faire que pour les nouvelles tables.  
  
 **Supprimer**  
 Sélectionnez une table dans la liste et cliquez sur **Supprimer** pour supprimer la table de l’instance CDC.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment modifier les propriétés d’Instance de capture de données modifiées](../../integration-services/change-data-capture/how-to-edit-the-cdc-instance-properties.md)   
 [Sélectionnez les colonnes et les Tables Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  

