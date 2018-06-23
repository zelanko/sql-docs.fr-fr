---
title: Nom correspondant (Assistant sources de données) (Analysis Services) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.datasourceviewwizard.namematchingcriteria.f1
ms.assetid: 7f811e02-0fe6-45c9-a7b7-29c61032d96b
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fcb6d01f55b450326efdea81d48135088d57fc3d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044850"
---
# <a name="name-matching-data-source-view-wizard-analysis-services"></a>Correspondance de noms (Assistant Vue de source de données) (Analysis Services)
  Utilisez la page **Correspondance de noms** pour sélectionner le critère à utiliser pour détecter les relations possibles entre les tables que vous sélectionnez pour la vue de source de données et les autres tables du schéma. Si aucune relation de clé étrangère n'existe entre les tables, ce critère permet d'identifier et d'ajouter les tables associées à la vue de source de données. Les relations logiques identifiées par une correspondance de noms sont également ajoutées à la vue de source de données.  
  
> [!NOTE]  
>  Cette page apparaît uniquement si vous sélectionnez une source de données qui dispose de plusieurs tables, mais pas de relations de clés étrangères entre les tables.  
  
## <a name="options"></a>Options  
 **Créer des relations logiques en faisant correspondre les colonnes**  
 Sélectionnez cette option pour utiliser un critère de correspondance de noms pour détecter les dépendances logiques et les relations possibles entre les tables que vous sélectionnez pour les inclure dans la vue de source de données et les autres tables du schéma. Si vous désactivez cette case à cocher, aucun critère de correspondance de noms n'est utilisé pour identifier les relations logiques entre les tables dans la source de données.  
  
 **Correspondances de clés étrangères**  
 Sélectionnez le critère à utiliser pour créer des relations logiques entre les tables et les vues dans la source de données. Les caractères non alphanumériques sont ignorés dans les chaînes de correspondance. Par exemple, « ID Client », « ID_Client », « IDClient » correspondent tous. Sélectionnez l'une des options suivantes dans le tableau ci-dessous pour créer des relations dans les cas indiqués.  
  
|Select|Élément créé|  
|------------|---------------|  
|**Nom identique à la clé primaire**|Relation logique à une table avec un nom de colonne qui correspond au nom de la colonne clé primaire d'une table sélectionnée.|  
|**Nom identique à celui de la table de destination**|Relation logique à une table avec un nom de colonne qui correspond au nom de la table sélectionnée.|  
|**Nom de la table de destination + nom de la clé primaire**|Relation logique à une table dans laquelle un nom de colonne correspond au nom de la table sélectionné concaténé avec le nom de la colonne clé primaire de la table sélectionnée (dans cet ordre). Les caractères non alphanumériques dans la concaténation sont ignorés (par exemple, « ID Produit », « ID_Produit » et « IDProduit » correspondent tous).|  
  
 **Description et exemple**  
 Affichage de la description et d'un exemple du critère sélectionné.  
  
  