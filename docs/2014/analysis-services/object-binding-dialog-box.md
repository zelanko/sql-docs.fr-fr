---
title: Objet boîte de dialogue liaison | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab14c0aad6701311e4ae9bc59679daca566bcdde
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099329"
---
# <a name="object-binding-dialog-box"></a>Boîte de dialogue Liaison d'objets
  Utilisez la boîte de dialogue **Liaison d'objets** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir des liaisons entre la propriété d'un objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et une table ou une colonne dans une vue de source de données. Pour afficher la boîte de dialogue **Liaison d’objets** , sélectionnez **(nouvelle)** dans la liste déroulante pour la valeur des propriétés suivantes d’un objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]:  
  
-   NameColumn  
  
-   ValueColumn  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   UnaryOperatorColumn  
  
## <a name="options"></a>Options  
 **Type de liaison**  
 Sélectionne la liaison à utiliser pour l'objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Les types de liaisons suivants peuvent être utilisés :  
  
 Liaison de colonne  
 Lie l'objet à une table et colonne existantes au sein d'une vue de source de données.  
  
 Générer une colonne  
 Indique qu'une nouvelle colonne doit être définie dans la vue de source de données et qu'une liaison de colonne lui sera ensuite associée.  
  
> [!NOTE]  
>  Si cette option est sélectionnée, vous devez exécuter **l’Assistant Génération de schéma** avant de déployer l’objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 Liaison de lignes  
 Lie l'objet à une ligne dans une table de faits et permet de faciliter les mesures de comptage en fonction du nombre de lignes traitées dans la table de faits.  
  
 **Table source**  
 Affiche la liste des tables de la vue de source de données associée à l’objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Colonne source**  
 Affiche la liste des colonnes de la table sélectionnée dans le champ **Table source**.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
