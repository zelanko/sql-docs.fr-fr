---
title: Modifier des tables | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2eaf455da969e1b8a50a2c174aefeec3aef40666
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728890"
---
# <a name="edit-tables"></a>Modifier des tables

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Utilisez l'onglet **Tables** pour apporter des modifications aux tables et aux colonnes sélectionnées dans la base de données source Oracle. Cet onglet contient les éléments suivants :  
  
 **Liste Table**  
 La liste de tables comporte trois colonnes :  
  
-   **Nom de la table Oracle** : Nom de la table, y compris du schéma de la table.  
  
-   **Instance de capture** : Nom de l’instance de capture utilisée pour nommer les objets de capture de données modifiées spécifiques à l’instance. L'instance de capture ne peut pas être NULL. S'il n'est pas spécifié, le nom est dérivé du nom de schéma d'origine associé au nom de table source au format `<schema-name>_<table-name>.` . Le nom de l'instance de capture ne peut pas dépasser 100 caractères et doit être unique dans la base de données. Vous pouvez cliquer dans n’importe quelle cellule de cette colonne pour modifier manuellement **capture_instance**.  
  
-   **Rôle de sécurité** : Nom du rôle de base de données utilisé pour obtenir l'accès aux données modifiées. Vous pouvez cliquer dans n’importe quelle cellule de cette colonne pour modifier manuellement **security_role**.  
  
 **Ajouter des tables**  
 Cliquez sur **Ajouter des tables** pour ouvrir la boîte de dialogue Sélection de table dans laquelle vous pouvez [ajouter des tables à une instance de capture de données modifiées](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md). Lorsque vous accédez pour la première fois à la base de données Oracle, vous devez [Connect to Oracle](../../integration-services/change-data-capture/connect-to-oracle.md).  
  
 **Modifier**  
 Sélectionnez une table dans la liste et cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Propriétés** de cette table dans laquelle vous pouvez [Modifier les propriétés d’une table](../../integration-services/change-data-capture/edit-the-table-properties.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas modifier le mappage de type pour les tables qui possèdent déjà des tables miroir. Vous ne pouvez le faire que pour les nouvelles tables.  
  
 **Supprimer**  
 Sélectionnez une table dans la liste et cliquez sur **Supprimer** pour supprimer la table de l’instance CDC.  
  
## <a name="see-also"></a> Voir aussi  
 [Procédure : modifier les propriétés d'une instance de capture de données modifiées](../../integration-services/change-data-capture/how-to-edit-the-cdc-instance-properties.md)   
 [Sélectionner des tables et des colonnes Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  
