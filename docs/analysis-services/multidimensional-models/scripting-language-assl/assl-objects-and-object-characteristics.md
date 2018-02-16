---
title: "Objets ASSL et caractéristiques de l’objet | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- reference exceptions [Analysis Services Scripting Language]
- ASSL, objects
- inheritance [Analysis Services Scripting Language]
- localized names [Analysis Services Scripting Language]
- objects [Analysis Services Scripting Language]
- names [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
- expansion [Analysis Services Scripting Language]
ms.assetid: 6e5c28b5-c0bc-4ccd-82e5-e174bbb71386
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 51c9b6140396cfc5080e3aee21cd8e708c05eb69
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="assl-objects-and-object-characteristics"></a>Objets ASSL et caractéristiques des objets
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Dans le langage ASSL (Analysis Services Scripting Language), les objets suivent des recommandations spécifiques en ce qui concerne les groupes d'objets, l'héritage, l'affectation de noms, l'expansion et le traitement.  
  
## <a name="object-groups"></a>Groupes d'objets  
 Tous les [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objets ont une représentation XML. Les objets se répartissent en deux groupes :  
  
 **Objets principaux**  
 Les objets principaux peuvent être créés, modifiés et supprimés de manière indépendante. Les objets principaux sont représentés par les éléments suivants :  
  
-   Serveurs  
  
-   Bases de données  
  
-   Dimensions  
  
-   Cubes  
  
-   les groupes de mesures ;  
  
-   Partitions  
  
-   Perspectives  
  
-   Modèles d'exploration de données  
  
-   Rôles  
  
-   Commandes associées à un serveur ou à une base de données  
  
-   Sources de données  
  
 Les objets principaux s'appuient sur les propriétés suivantes pour suivre leur historique et leur état :  
  
-   **CreatedTimestamp**  
  
-   **LastSchemaUpdate**  
  
-   **LastProcessed** (le cas échéant)  
  
> [!NOTE]  
>  La classification d'un objet comme objet principal a un effet sur la façon dont une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] traite cet objet et sur la façon dont il est traité dans le langage de définition d'objet. Toutefois, cette classification ne garantit pas que les outils de gestion et de développement [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] permettront de créer, modifier ou supprimer ces objets de manière indépendante.  
  
 **Objets secondaires**  
 Les objets secondaires ne peuvent être créés, modifiés ou supprimés que dans la cadre de la création, de la modification ou de la suppression de l'objet principal parent. Les objets secondaires sont représentés par les éléments suivants :  
  
-   Hiérarchies et niveaux  
  
-   Attributs  
  
-   Mesures  
  
-   Colonnes de modèle d'exploration de données  
  
-   Commandes associées à un cube  
  
-   Aggregations  
  
## <a name="object-expansion"></a>Expansion d'objet  
 La restriction **ObjectExpansion** peut être utilisée pour contrôler le degré d'expansion des éléments XML ASSL retournés par le serveur. Cette restriction propose les options répertoriées dans le tableau suivant.  
  
|Valeur d'énumération|Autorisé pour \<Alter >| Description|  
|-----------------------|---------------------------|-----------------|  
|*ReferenceOnly*|non|Retourne uniquement le nom, l'ID et l'horodateur pour l'objet demandé et tous les objets principaux qu'il contient de manière récursive.|  
|*ObjectProperties*|oui|Développe l'objet demandé et les objets secondaires qu'il contient, mais ne retourne pas les objets principaux qu'il contient.|  
|*ExpandObject*|non|Identique à *ObjectProperties*, mais retourne également le nom, l'ID et l'horodateur pour les objets principaux contenus.|  
|*ExpandFull*|oui|Développe entièrement l'objet demandé et touts les objets qu'il contient de manière récursive.|  
  
 Cette section de référence ASSL décrit la représentation *ExpandFull* . Tous les autres niveaux **ObjectExpansion** sont dérivés de ce niveau.  
  
## <a name="object-processing"></a>Traitement des objets  
 ASSL inclut des éléments en lecture seule ou des propriétés (par exemple, **LastProcessed**) qui peuvent être lus à partir de la [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance, mais qui sont omis lorsque des scripts de commande sont soumis à l’instance. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignore les valeurs modifiées pour les éléments en lecture seule sans émettre d'avertissement ni d'erreur.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignore également les propriétés non appropriées ou non pertinentes sans déclencher d'erreurs de validation. Par exemple, l'élément X ne doit être présent que lorsque l'élément Y a une valeur particulière. L'instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ignore l'élément X au lieu de le valider par rapport à la valeur de l'élément Y.  
  
  
