---
title: Modifier la propriété KeyColumn d’un attribut | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- binding attributes [Analysis Services]
- attributes [Analysis Services], binding
- key columns [Analysis Services]
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
author: minewiskan
ms.author: owend
ms.openlocfilehash: ad5674f576f7a6cf42b396d3e76db457f068e1ee
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544761"
---
# <a name="modify-the-keycolumn-property-of-an-attribute"></a>Modifier la propriété KeyColumn d'un attribut
  Vous pouvez modifier la propriété **KeyColumns** d'un attribut. Par exemple, vous souhaiterez peut-être spécifier une clé composite plutôt qu'une clé unique comme clé de l'attribut.  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a>Pour modifier la propriété KeyColumns d'un attribut  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet dont vous souhaitez modifier la propriété **KeyColumns** .  
  
2.  Ouvrez le Concepteur de dimensions en suivant l'une des procédures ci-dessous :  
  
    -   Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la dimension dans le dossier **Dimensions** , puis cliquez sur **Ouvrir** ou **Concepteur de vues**.  
  
         -ou-  
  
    -   Dans le concepteur de cube, sous l’onglet **structure de cube** , développez la dimension de cube dans le volet **dimensions** , puis cliquez sur **modifier \<dimension> **.  
  
3.  Sous l'onglet **Structure de dimension** , dans le volet **Attributs** , cliquez sur l'attribut dont vous souhaitez modifier la propriété **KeyColumns** .  
  
4.  Dans la fenêtre **Propriétés** , cliquez sur la valeur de la propriété **KeyColumns** .  
  
5.  Cliquez sur le bouton Parcourir **(...)** qui apparaît dans la cellule de la valeur de la zone de propriété.  
  
     La boîte de dialogue de **Colonnes clés** s'ouvre.  
  
6.  Pour supprimer une colonne clé existante, sélectionnez la colonne dans la liste **Colonnes clés** , puis cliquez sur le bouton **\<** .  
  
7.  Pour ajouter une colonne clé, sélectionnez la colonne dans la liste **Colonnes disponibles** , puis cliquez sur le bouton **>** .  
  
    > [!NOTE]  
    >  Si vous définissez plusieurs colonnes clés, l'ordre dans lequel ces colonnes apparaissent dans la liste **Colonnes clés** affecte l'ordre d'affichage. Par exemple, un attribut de mois a deux colonnes clés : mois et année. Si la colonne d'année apparaît dans la liste avant la colonne de mois, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] triera par année, puis par mois. Si la colonne de mois apparaît avant la colonne d'année, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] triera par mois, puis par année.  
  
8.  Pour modifier l'ordre des colonnes clés, sélectionnez une colonne, puis cliquez le bouton **Haut** ou **Bas** .  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des propriétés d’attribut de dimension](dimension-attribute-properties-reference.md)  
  
  
