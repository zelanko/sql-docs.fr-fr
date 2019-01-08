---
title: Modifier des tables | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: acb954cd9193d5c6132a8d2d081250a8ecdff562
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52770831"
---
# <a name="edit-tables"></a>Modifier des tables
  Utilisez l'onglet **Tables** pour apporter des modifications aux tables et aux colonnes sélectionnées dans la base de données source Oracle. Cet onglet contient les éléments suivants :  
  
 **Liste Table**  
 La liste de tables comporte trois colonnes :  
  
-   **Nom de la Table Oracle**: Le nom de la table, y compris le schéma de table.  
  
-   **Instance de capture**: Le nom de l’instance de capture utilisée pour nommer des objets de capture de données de modification de spécifique à l’instance. L'instance de capture ne peut pas être NULL. S'il n'est pas spécifié, le nom est dérivé du nom de schéma d'origine associé au nom de table source au format `<schema-name>_<table-name>.` . Le nom de l'instance de capture ne peut pas dépasser 100 caractères et doit être unique dans la base de données. Vous pouvez cliquer dans n’importe quelle cellule de cette colonne pour modifier manuellement **capture_instance**.  
  
-   **Rôle de sécurité**: Le nom du rôle de base de données utilisé pour accéder aux données modifiées. Vous pouvez cliquer dans n’importe quelle cellule de cette colonne pour modifier manuellement **security_role**.  
  
 **Ajouter des tables**  
 Cliquez sur **Ajouter des tables** pour ouvrir la boîte de dialogue Sélection de table dans laquelle vous pouvez [ajouter des tables à une instance de capture de données modifiées](add-tables-to-a-cdc-instance.md). Lorsque vous accédez pour la première fois à la base de données Oracle, vous devez [Connect to Oracle](connect-to-oracle.md).  
  
 **Modifier**  
 Sélectionnez une table dans la liste et cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Propriétés** de cette table dans laquelle vous pouvez [Modifier les propriétés d’une table](edit-the-table-properties.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas modifier le mappage de type pour les tables qui possèdent déjà des tables miroir. Vous ne pouvez le faire que pour les nouvelles tables.  
  
 **Supprimer**  
 Sélectionnez une table dans la liste et cliquez sur **Supprimer** pour supprimer la table de l’instance CDC.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : modifier les propriétés d'une instance de capture de données modifiées](how-to-edit-the-cdc-instance-properties.md)   
 [Sélectionner des tables et des colonnes Oracle](select-oracle-tables-and-columns.md)  
  
  
