---
title: "Objet de modèle (TMSL) | Documents Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9382d0d6-2d4b-49ad-a0eb-35970f0f3afb
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 369bf544360d50c061314f45c04e8fb55784184c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="model-object-tmsl"></a>Objet de modèle (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Définit un modèle tabulaire. Il existe un modèle par base de données et qu’une seule base de données qui peut être spécifié dans n’importe quelle commande donnée. Un objet de base de données est l’objet parent.  
  
 Les définitions de modèle sont trop volumineuses pour reproduire la syntaxe ensemble dans une rubrique. Pour cette raison, une mise en évidence les principaux éléments de syntaxe partielle peut trouver ci-dessous, avec des liens vers les objets enfants.  
  
 La meilleure façon de comprendre une définition de modèle est peut-être commencer par un modèle tabulaire que vous connaissez bien. Utilisez le **afficher le Code** option dans SQL Server Data Tools pour afficher sa définition. N’oubliez pas d’installer un éditeur JSON afin que vous pouvez afficher le code. Vous pouvez obtenir un éditeur JSON dans Visual Studio en [du téléchargement de l’édition Community](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) ou autre édition de Visual Studio.  
  
> [!NOTE]  
>  Dans n’importe quel script, qu’une seule base de données en temps peut être référencée. Pour les objets autres que de base de données elle-même, la propriété de base de données est facultative si vous spécifiez le modèle. Il existe un mappage entre un modèle et une base de données qui peut être utilisé pour déduire le nom de la base de données si elle n’est pas explicitement fourni.   
> De même, vous pouvez laisser le modèle, définissant ses propriétés dans la base de données.  
  
## <a name="object-definition"></a>Définition de l'objet  
 Tous les objets ont un ensemble commun de propriétés, y compris le nom, type, la description, une collection de propriétés et annotations. **Modèle** objets ont également les propriétés suivantes.  
  
 storageLocation  
 L’emplacement sur le disque pour placer le modèle.  
  
 defaultMode  
 La méthode par défaut pour rendre les données disponibles dans la partition.  
  
 defaultDataView  
 Pour les modèles en mode DirectQuery, cette propriété détermine les partitions sont utilisées pour exécuter des requêtes sur le modèle.  Les valeurs valides sont Full et exemple.  
  
 culture  
 La culture à utiliser pour mettre en forme.  
  
 collation  
 La séquence de classement. Consultez [des scénarios de globalisation pour Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md) pour plus d’informations.  
  
 tables  
 La collection complète des tables dans le modèle, y compris les partitions, les colonnes, les mesures, les indicateurs de performance clés et les annotations. Consultez [Tables objet &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) pour plus d’informations.  
  
 relations  
 Spécifie la relation entre chaque paire de tables, y compris les propriétés qui définissent la direction du filtrage et sécurité. Consultez [objet de relations &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md) pour plus d’informations.  
  
 sources de données  
 Une ou plusieurs connexions à des bases de données externes fournissant des données au modèle ou utilisé pour traversent les requêtes. Consultez [sources de données objet &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md) pour plus d’informations.  
  
 rôles  
 Objets qui associent une autorisation de base de données, les comptes de membre et le cas échéant, les filtres de sécurité dans DAX pour le contrôle d’accès personnalisés.  
  
## <a name="usage"></a>Utilisation  
 **Modèle** objets contiennent un modèle entier. Vous devez spécifier un modèle et/ou de son objet de base de données parent dans la plupart des commandes.  
  
 Lors de la création, du remplacement ou de modification d’un objet de modèle, spécifiez toutes les propriétés en lecture-écriture de la définition d’objet. L’omission d’une propriété en lecture-écriture est considérée comme une suppression.  
  
## <a name="partial-syntax"></a>Syntaxe partielle  
 Étant donné que cette définition de l’objet est tellement importante, les propriétés de niveau premier sont répertoriées. Consultez [définitions d’objets dans le tableau de modèle un langage de script &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) pour obtenir la liste d’objets enfants.  
  
```  
    "model": {  
      "description": "Model object of a Tabular database",  
      "type": "object",  
      "properties": {  
          "name": {  },  
          "description": {  },  
         "storageLocation": {  },  
         "defaultMode":  {  },  
         "defaultDataView": {  },  
         "culture": {  },  
         "collation": {  },  
         "annotations": {  },  
         "tables": {  },  
         "relationships": {  },  
         "dataSources": {  },  
         "perspectives": {  },  
            "cultures": {  },  
         "roles": {  }  
    }  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference [Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;]](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  

