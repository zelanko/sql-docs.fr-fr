---
title: Créer modifier nommé de la boîte de dialogue calcul (Analysis Services) | Documents Microsoft
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
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 007fce8fae62df381629b4daa1b6ef0c00d781bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038480"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a>Créer-modifier la boîte de dialogue calcul nommé (Analysis Services)
  Utilisez la boîte de dialogue **Créer un calcul nommé/Modifier le calcul nommé** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir ou modifier un calcul nommé d’une table dans une vue de source de données. Vous pouvez afficher la boîte de dialogue **Créer un calcul nommé/Modifier le calcul nommé** en :  
  
-   cliquant sur **Nouveau calculé nommé** dans le volet **Barre d’outils** du **Concepteur de vue de source de données** ;  
  
-   cliquant avec le bouton droit sur une table dans le volet **Tables** ou **Schéma** du **Concepteur de vue de source de données** et en sélectionnant **Nouveau calcul nommé** ;  
  
-   cliquant avec le bouton droit sur le nom d’un calcul nommé dans le volet **Schéma** du **Concepteur de vue de source de données** et en sélectionnant **Modifier le calcul nommé**.  
  
## <a name="options"></a>Options  
 **Nom de la colonne**  
 Entrez le nom du calcul nommé.  
  
 **Description**  
 Entrez la description facultative du calcul nommé.  
  
 **Expression**  
 Entrez une expression SQL valide qui retourne une valeur scalaire. L'expression est envoyée au fournisseur et validée dans l'expression suivante :  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 L'expression peut contenir des références à d'autres tables via une instruction sub-select. If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Concepteur de vue de Source de données &#40;Analysis Services - données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  