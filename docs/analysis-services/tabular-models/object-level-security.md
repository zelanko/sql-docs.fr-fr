---
title: Sécurité au niveau de l’objet de modèle tabulaire à Analysis Services | Microsoft Docs
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: d354aa64e8b6a1e98941011c30550a056f4c01c9
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685575"
---
# <a name="object-level-security"></a>Sécurité au niveau des objets
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Sécurité de modèle de données commence par l’implémentation efficace de [rôles](../../analysis-services/tabular-models/roles-ssas-tabular.md) et les filtres au niveau des lignes pour définir les autorisations utilisateur sur les objets de modèle de données et des données. À partir de modèles tabulaires 1400, vous pouvez également définir au niveau de l’objet de sécurité, qui inclut la sécurité au niveau de la table et la sécurité au niveau des colonnes dans le [Roles, objet](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl).

## <a name="table-level-security"></a>Sécurité au niveau des tables

Avec la sécurité au niveau de la table, vous pouvez restreindre pas uniquement l’accès aux données de table, mais également les noms de tables sensibles, aider à empêcher les utilisateurs malveillants de découvrir si une table existe. 

 Sécurité au niveau de la table est définie dans les métadonnées basé sur JSON dans Model.bim, [tabulaire modèle Scripting Language (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference), ou [le modèle d’objet tabulaire (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo). Définir le **metadataPermission** propriété de la **autorisations de table** classe dans le [Roles, objet](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl) à **aucun**.

Dans cet exemple, la propriété metadatapermission alors que de la classe d’autorisations de table pour la table Product est définie sur none :

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Product",
        "metadataPermission": "none"
      }
    ]
  }
```

## <a name="column-level-security"></a>Sécurité au niveau de la colonne

Similaire à la sécurité au niveau table, avec la sécurité au niveau de la colonne vous pas uniquement restreignent l’accès aux données de la colonne, mais également les noms des colonnes sensibles, aider à empêcher les utilisateurs malveillants de découvrir une colonne.

 Sécurité au niveau de la colonne est définie dans les métadonnées basé sur JSON dans Model.bim, [tabulaire modèle Scripting Language (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference), ou [le modèle d’objet tabulaire (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo). Définir le **metadataPermission** propriété de la **columnPermissions** classe dans le [Roles, objet](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl) à **aucun**.

Dans cet exemple, la propriété metadatapermission alors que de la classe columnPermissions pour la colonne de taux de Base dans la table Employees est définie sur none :

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Employee",
        "columnPermissions": [
          {
            "name": "Base Rate",
            "metadataPermission": "none"
          }
        ]
      }
    ]
  }
```

## <a name="restrictions"></a>Restrictions

*  Impossible de définir la sécurité au niveau de la table pour un modèle si elle s’arrête une chaîne de relation. Une erreur est générée au moment du design.
 Par exemple, s’il existe des relations entre des tables A et B et B et C, vous ne pouvez pas sécuriser la table B. Si la table B est sécurisée, une requête sur la table A ne peuvent pas transiter les relations entre la table A et B et B et C. Dans ce cas, une relation distincte peut être configurée entre les tables A et B.

    ![Sécurité au niveau des tables](../../analysis-services/tabular-models/media/ssas-ols.png)  


*  Sécurité de niveau ligne et la sécurité au niveau de l’objet ne peut pas être combinés à partir de différents rôles, car il pourrait induire l’accès involontaire à des données sécurisées. Une erreur est générée au moment de la requête pour les utilisateurs qui sont membres d’une telle combinaison des rôles.

*  Des calculs dynamiques (mesures, indicateurs de performance clés, DetailRows) sont automatiquement limitées si elles font référence à une table sécurisée ou une colonne. Il n’existe aucun mécanisme pour sécuriser explicitement une mesure, il est possible de sécuriser implicitement une mesure en mettant à jour de l’expression pour faire référence à une table sécurisée ou une colonne.

*  Les relations qui font référence à une colonne sécurisée de travail fournie par la table dans la colonne n’est pas sécurisée.




## <a name="see-also"></a>Voir aussi  
[Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
[Roles, objet (TMSL)](https://docs.microsoft.com/bi-reference/tmsl/roles-object-tmsl)  
[Langage TMSL (Tabular Model Scripting Language)](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)  
[Modèle d’objet tabulaire (TOM)](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).

  
