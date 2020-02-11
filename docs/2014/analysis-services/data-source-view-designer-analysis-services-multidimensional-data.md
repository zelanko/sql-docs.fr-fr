---
title: Concepteur de vue de source de données (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.f1
helpviewer_keywords:
- Data Source View Designer
ms.assetid: 6f40a074-761f-440b-a999-09b755bd86ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9153a2d07653872ca6ce1f90e39c90f32da21fba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082523"
---
# <a name="data-source-view-designer-analysis-services---multidimensional-data"></a>Concepteur de vue de source de données (Analysis Services - Données multidimensionnelles)
  Une vue de source de données (DSV) est une vue logique d'une source de données relationnelle externe utilisée pour créer des cubes et des dimensions dans un modèle multidimensionnel.  
  
 Une fois qu'une vue a été générée, vous pouvez utiliser le **Concepteur de vue de source de données** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour travailler directement sur la vue de source de données, ce qui peut être utile s'il manque à la source de données sous-jacente les éléments de données nécessaires à un modèle multidimensionnel.  
  
 Pour ouvrir le **Concepteur de vue de source de données** :  
  
-   Double-cliquez sur une vue de source de données dans **l’Explorateur de solutions**.  
  
-   Cliquez avec le bouton droit sur une vue de source de données dans **l’Explorateur de solutions** et sélectionnez **Ouvrir** ou **Concepteur de vues**.  
  
 Le **Concepteur de vue de source de données** contient une barre d'outils, un diagramme montrant les objets et les relations dans la vue de source de données, un volet de table répertoriant les tables et les requêtes nommées par ordre alphabétique, ainsi qu'un volet Bibliothèque de diagrammes utilisé pour créer et afficher les diagrammes spécifiques de la vue. Vous pouvez cliquer avec le bouton droit sur une table ou une relation afin d'accéder à des commandes contextuelles.  
  
 ![Concepteur de vue de source de données](media/ssas-dsvdesigner.PNG "Concepteur de vue de source de données")  
  
 Au minimum, une vue de source de données affiche les tables de la base de données relationnelle qui seront utilisées pour remplir les objets de modèle lors du traitement. Un vue de source de données est générée, généralement à l'aide de l'Assistant Vue de source de données. Les tables, colonnes et relations de la vue de source de données deviennent la base des dimensions et des mesures dans un cube. Une fois que la vue de source de données est créée, vous pouvez utiliser le concepteur de vue de source de données pour la modifier.  
  
 La plupart des développeurs Analysis Services utilisent une vue de source de données générée telle quelle, avec un nombre réduit de personnalisations. C'est notamment le cas si les données sources proviennent d'une vue d'une base de données SQL Server. Dans ce cas, vous préférerez peut-être gérer les relations de données et les calculs dans une vue T-SQL plutôt que dans une vue de source de données Analysis Services. Cependant, si vous n'êtes pas propriétaire de la base de données sous-jacente, vous pouvez modifier la vue de source de données dans Analysis Services afin de développer davantage les structures de données utilisées dans votre modèle.  
  
## <a name="tasks-in-data-source-view-designer"></a>Tâches dans le concepteur de vue de source de données  
 Le concepteur de vue de source de données vous permet d'effectuer les modifications suivantes dans une vue de source de données :  
  
|||  
|-|-|  
|Renommer des colonnes ou des tables, ou encore créer des colonnes calculées. Par exemple, concaténez un prénom et un nom dans une nouvelle colonne de nom et prénom.|[Définir des calculs nommés dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)|  
|Ajouter manuellement des relations entre tables|[Définir des relations logiques dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/define-logical-relationships-in-a-data-source-view-analysis-services.md)|  
|Créer une requête nommée pour définir un nouvel objet basé sur une requête T-SQL.|[Définir des requêtes nommées dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)|  
|Explorer les données sous-jacentes pour afficher les valeurs de données réelles représentées par les objets de modèle.<br /><br /> L'exploration de données vous permet d'inspecter visuellement et de copier les données retournées à partir de la table ou de la requête dimensionnelle sous-jacente. Par défaut, l'exploration de données utilise la méthode d'échantillonnage « Les premières » qui échantillonne les 5000 premières lignes, mais vous pouvez modifier ces paramètres.|[Explorez les données dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/explore-data-in-a-data-source-view-analysis-services.md)|  
|Représenter sous forme de diagramme tout ou partie des tables et des relations dans une vue de source de données|[Utiliser des diagrammes dans le concepteur de vue de source de données &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Ajout ou suppression de tables ou de vues dans une vue de source de données &#40;Analysis Services&#41;](multidimensional-models/adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)  
  
  
