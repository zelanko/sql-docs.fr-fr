---
title: "Modifier la propri&#233;t&#233; KeyColumn d&#39;un attribut | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "liaison d'attributs [Analysis Services]"
  - "attributs [Analysis Services], liaison"
  - "colonnes clés [Analysis Services]"
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Modifier la propri&#233;t&#233; KeyColumn d&#39;un attribut
  Vous pouvez modifier la propriété **KeyColumns** d'un attribut. Par exemple, vous souhaiterez peut-être spécifier une clé composite plutôt qu'une clé unique comme clé de l'attribut.  
  
### Pour modifier la propriété KeyColumns d'un attribut  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet dont vous souhaitez modifier la propriété **KeyColumns** .  
  
2.  Ouvrez le Concepteur de dimensions en suivant l'une des procédures ci-dessous :  
  
    -   Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la dimension dans le dossier **Dimensions**, puis cliquez sur **Ouvrir** ou **Concepteur de vues**.  
  
         —ou—  
  
    -   Dans le Concepteur de cube, sous l’onglet **Structure de cube**, développez la dimension de cube dans le volet **Dimensions** et cliquez sur **Modifier \<dimension>**.  
  
3.  Sous l'onglet **Structure de dimension** , dans le volet **Attributs** , cliquez sur l'attribut dont vous souhaitez modifier la propriété **KeyColumns** .  
  
4.  Dans la fenêtre **Propriétés** , cliquez sur la valeur de la propriété **KeyColumns** .  
  
5.  Cliquez sur le bouton Parcourir **(...)** qui apparaît dans la cellule de la valeur de la zone de propriété.  
  
     La boîte de dialogue de **Colonnes clés** s'ouvre.  
  
6.  Pour supprimer une colonne clé existante, sélectionnez la colonne dans la liste **Colonnes clés**, puis cliquez sur le bouton **\<**.  
  
7.  Pour ajouter une colonne clé, sélectionnez la colonne dans la liste **Colonnes disponibles**, puis cliquez sur le bouton **>**.  
  
    > [!NOTE]  
    >  Si vous définissez plusieurs colonnes clés, l'ordre dans lequel ces colonnes apparaissent dans la liste **Colonnes clés** affecte l'ordre d'affichage. Par exemple, un attribut de mois a deux colonnes clés : mois et année. Si la colonne d'année apparaît dans la liste avant la colonne de mois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] triera par année, puis par mois. Si la colonne de mois apparaît avant la colonne d'année, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] triera par mois, puis par année.  
  
8.  Pour modifier l'ordre des colonnes clés, sélectionnez une colonne, puis cliquez le bouton **Haut** ou **Bas** .  
  
## Voir aussi  
 [Référence des propriétés d'attribut de dimension](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  