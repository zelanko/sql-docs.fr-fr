---
title: Présentation des schémas de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Schema Generation Wizard, database schema
- database schema [Analysis Services]
- relational schema [Analysis Services], database schema
- subject area schema options [Analysis Services]
- staging area schema options [Analysis Services]
- denormalized schemas
ms.assetid: 51e411f9-ee3f-4b92-9833-c2bce8c6b752
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 554f226c3b6ca1fa3a753947b08a3fea3d6946c6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740751"
---
# <a name="understanding-the-database-schemas"></a>Présentation des schémas de base de données
  L'Assistant Génération de schéma crée pour la base de données de la zone de sujet un schéma relationnel dénormalisé basé sur les dimensions et les groupes de mesures définis dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. L'Assistant génère pour chaque dimension une table relationnelle appelée table de dimension, destinée à stocker les données de dimension, et pour chaque groupe de mesures une table relationnelle appelée table de faits, servant à stocker les données de faits. Lorsqu'il génère ces tables relationnelles, l'Assistant ignore les dimensions liées, les groupes de mesures liés et les dimensions de temps de serveur.  
  
## <a name="validation"></a>Validation  
 Avant de commencer à générer le schéma relationnel sous-jacent, l'Assistant Génération de schéma valide les cubes et les dimensions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Si l'Assistant détecte des erreurs, il s'arrête et signale ces erreurs dans la fenêtre Liste des tâches de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Voici quelques exemples d'erreurs qui empêchent la génération :  
  
-   Les dimensions qui ont plus d'un attribut clé.  
  
-   Les attributs parents qui ont des types de données différents de ceux des attributs clés.  
  
-   Les groupes de mesures dépourvus de mesures.  
  
-   Les dimensions dégénérées ou les mesures mal configurées.  
  
-   Les clés de substitution mal configurées, par exemple plusieurs attributs utilisant le type d'attribut `ScdOriginalID` ou un attribut utilisant le type `ScdOriginalID` sans être lié à une colonne utilisant le type de données Integer.  
  
## <a name="dimension-tables"></a>Tables de dimension  
 Pour chaque dimension, l'Assistant Génération de schéma crée une table de dimension à inclure dans la base de données de la zone de sujet. La structure de la table de dimension dépend des choix effectués lors de la conception de la dimension sur laquelle elle est basée.  
  
 Colonnes  
 L'Assistant génère une colonne pour les liaisons associées à chaque attribut de la dimension sur laquelle la table de dimension est basée, par exemple les liaisons pour les propriétés `KeyColumns`, `NameColumn`, `ValueColumn`, `CustomRollupColumn`, `CustomRollupPropertiesColumn` et `UnaryOperatorColumn` de chaque attribut.  
  
 Relations  
 L'Assistant génère une relation entre la colonne de chaque attribut parent et la clé primaire de la table de dimension.  
  
 L'Assistant crée également, s'il y a lieu, une relation à la clé primaire de chaque table de dimension supplémentaire définie comme dimension référencée du cube.  
  
 Contraintes  
 L'Assistant génère par défaut pour chaque table de dimension une contrainte de clé primaire basée sur l'attribut clé de la dimension. Si la contrainte de clé primaire est générée, une colonne de nom séparée est créée par défaut. Une clé primaire logique est créée dans la vue de source de données même si vous décidez de ne pas créer la clé primaire dans la base de données.  
  
> [!NOTE]  
>  Une erreur se produit si plusieurs attributs clés sont spécifiés dans la dimension sur laquelle la table de dimension est basée.  
  
 Translations  
 L'Assistant génère une table séparée pour stocker les valeurs traduites de tout attribut qui nécessite une colonne de traduction. L'Assistant crée également une colonne séparée pour chacune des langues requises.  
  
## <a name="fact-tables"></a>Tables de faits  
 Pour chaque groupe de mesures d'un cube, l'Assistant Génération de schéma crée une table de faits à inclure dans la base de données de la zone de sujet. La structure de la table de faits dépend des choix effectués lors de la conception du groupe de mesures sur lequel elle est basée et des relations établies entre le groupe de mesures et les dimensions incluses.  
  
 Colonnes  
 L'Assistant génère une colonne pour chaque mesure, sauf pour les mesures qui utilisent la fonction d'agrégation `Count`. En effet, de telles mesures ne nécessitent pas de colonne correspondante dans la table de faits.  
  
 L'Assistant génère également une colonne pour chaque colonne d'attribut de granularité de chaque relation de dimension régulière du groupe de mesures et, s'il y a lieu, une ou plusieurs colonnes pour les liaisons associées à chaque attribut d'une dimension qui entretient une relation de dimension de fait avec le groupe de mesures sur lequel cette table est basée.  
  
 Relations  
 L'Assistant génère une relation pour chaque relation de dimension régulière de la table de faits à l'attribut de granularité de la table de la dimension. Si la granularité est basée sur l'attribut clé de la table de dimension, la relation est créée dans la base de données et dans la vue de source de données. Si la granularité est basée sur un autre attribut, la relation n'est créée que dans la vue de source de données.  
  
 Si vous choisissez de générer les index dans l'Assistant, un index non-cluster est créé pour chacune de ces colonnes de relation.  
  
 Contraintes  
 Les clés primaires ne sont pas générées sur les tables de faits.  
  
 Si vous choisissez d'appliquer l'intégrité référentielle, des contraintes d'intégrité référentielle sont générées, le cas échéant, entre les tables de dimension et les tables de faits.  
  
 Translations  
 L'Assistant génère une table séparée pour stocker les valeurs traduites de toute propriété du groupe de mesures qui nécessite une colonne de traduction. L'Assistant crée également une colonne séparée pour chacune des langues requises.  
  
## <a name="data-type-conversion-and-default-lengths"></a>Conversion de type de données et longueurs par défaut  
 Assistant génération de schéma ignore les types de données dans tous les cas sauf pour les colonnes qui utilisent le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar` type de données. Le type de données `wchar` se traduit directement en type de données `nvarchar`. Toutefois, si la longueur spécifiée d'une colonne utilisant le type `wchar` dépasse 4 000 octets, l'Assistant Génération de schéma produit une erreur.  
  
 Le tableau suivant indique la longueur par défaut de la colonne si un élément de données, par exemple la liaison d'un attribut, n'a pas de longueur spécifiée.  
  
|Élément de données|Longueur par défaut (en octets)|  
|---------------|------------------------------|  
|KeyColumn|50|  
|NameColumn|50|  
|CustomRollupColumn|3000|  
|CustomRollupPropertiesColumn|500|  
|UnaryOperatorColumn|1|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de la génération incrémentielle](understanding-incremental-generation.md)   
 [Gérer des modifications dans les vues de source de données et les sources de données](manage-changes-to-data-source-views-and-data-sources.md)  
  
  
