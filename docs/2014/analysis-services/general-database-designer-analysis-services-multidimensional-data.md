---
title: Général (Concepteur de bases de données) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.dbconfigurationpane.f1
helpviewer_keywords:
- Database Designer
ms.assetid: 00c9c42b-db2b-4620-8fb6-1e165ff0cbdd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e1e7b2e1e72263d8edf362941985bb775457fc6d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544472"
---
# <a name="general-database-designer-analysis-services---multidimensional-data"></a>Général (Concepteur de bases de données) (Analysis Services - Données multidimensionnelles)
  Utilisez l’onglet **Général** pour modifier les propriétés d’une base de données [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Pour afficher l'onglet Général**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
2.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , cliquez sur **Modifier la base de données**, puis sur l’onglet **Général** .  
  
## <a name="basic-options"></a>Options de base  
 Développez la section **De base** pour modifier les informations fondamentales sur la base de données. Cette section contient les options suivantes :  
  
 **Nom de la base de données**  
 Affiche le nom de la base de données.  
  
> [!NOTE]  
>  Pour renommer la base de données, dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**. Dans la page **Déploiement** de la boîte de dialogue **Pages de propriétés** de cette base de données, attribuez à la valeur de la propriété **Base de données** le nouveau nom de la base de données.  
  
 **Description**  
 Tapez la description de la base de données.  
  
## <a name="translations-options"></a>Options de traduction  
 Développez la section **Traductions** pour créer et modifier les traductions pour la légende et la description de la base de données. Cette section comprend une grille avec les colonnes suivantes :  
  
 **Langue**  
 Choisissez la langue de la transaction spécifiée.  
  
 Pour ajouter une nouvelle traduction à la grille, cliquez sur **\<Add new translation>** .  
  
 **Légende traduite**  
 Tapez la légende de la base de données dans la langue adéquate pour procéder à la traduction. Si vous ne renseignez pas ce champ, la légende par défaut est utilisée pour cette base de données.  
  
 **Description traduite**  
 Tapez la description de la base de données dans la langue adéquate pour procéder à la traduction. Si vous ne renseignez pas ce champ, la description par défaut est utilisée pour cette base de données.  
  
## <a name="account-type-mapping-options"></a>Options de mappage du type de compte  
 Développez la section **Mappage de type de compte** pour modifier la fonction d’agrégation par défaut associée à chaque **type** de compte dans la base de données sélectionnée.  
  
> [!NOTE]  
>  Cette option s’applique uniquement aux cubes, dans lesquels au moins une mesure utilise la fonction d’agrégation *ByAccount* .  
  
 Cette section comprend une grille avec les colonnes suivantes :  
  
 **Nom**  
 Tapez le nom du type de compte.  
  
 Pour ajouter un nouveau type de compte, cliquez sur **\<Add new account type>** .  
  
 **Alias**  
 Définit le nom par défaut du type de compte, à utiliser par l'Assistant Business Intelligence. Si cette colonne est laissée vide, la valeur par défaut dans la colonne **Nom** est utilisée.  
  
 **Fonction d’agrégation**  
 Sélectionnez la fonction d'agrégation à utiliser pour le type de compte sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Bases de données de modèle multidimensionnels &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)   
 [Avertissements &#40;concepteur de base de données&#41; &#40;Analysis Services-données multidimensionnelles&#41;](warnings-database-designer-analysis-services-multidimensional-data.md)  
  
  
