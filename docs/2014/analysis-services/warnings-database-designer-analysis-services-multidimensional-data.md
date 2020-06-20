---
title: Avertissements (Concepteur de bases de données) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.warnings.f1
ms.assetid: 13f58b4d-f345-4fbc-ae2d-b3c8290a797d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 113f644d9f1da48790e7c8d59d34e6b143a1175a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938120"
---
# <a name="warnings-database-designer-analysis-services---multidimensional-data"></a>Avertissements (Concepteur de bases de données) (Analysis Services - Données multidimensionnelles)
  L’onglet **Avertissements** permet d’afficher et d’ignorer des règles globalement, et d’afficher et de réactiver des instances spécifiques d’avertissements ignorés. L'onglet **Avertissements** affiche deux grilles : **Règles d'avertissements de conception** et **Avertissements ignorés**.  
  
 **Pour afficher l'onglet Avertissements**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
2.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur **Modifier la base de données**, puis sur l’onglet **Avertissements** .  
  
## <a name="design-warning-rules-grid"></a>Grille Règles d'avertissements de conception  
 La grille **Règles d'avertissements de conception** affiche toutes les règles d'avertissements de conception. Cette grille contrôle également les règles activées pour la base de données. Pour activer ou désactiver une règle d'avertissement, activez ou désactivez la case à cocher correspondante.  
  
 Les colonnes de la grille **Règles d'avertissements de conception** sont les suivantes :  
  
 **Description**  
 Affiche le nom de la règle. Les règles sont regroupées par catégorie.  
  
 **Importance**  
 Affiche l'importance affectée à la règle.  
  
 **Commentaires**  
 (Facultatif) Permet à l'utilisateur de taper un commentaire qui explique pourquoi vous ignorez l'avertissement.  
  
## <a name="dismissed-warnings-grid"></a>Grille Avertissements ignorés  
 La grille **Avertissements ignorés** affiche toutes les occurrences d'avertissements spécifiques qui ont été ignorées à partir de la **Liste d'erreurs**. Pour réactiver un avertissement, sélectionnez-le dans la grille, puis cliquez sur **Réactiver**.  
  
 Les colonnes de la grille **Avertissements ignorés** sont les suivantes :  
  
 **Object**  
 Affiche une icône qui représente le type d'objet et le nom d'objet.  
  
 **Type**  
 Affiche le type d'objet.  
  
 **Description**  
 Affiche le nom de la règle.  
  
 **Importance**  
 Affiche l'importance affectée à la règle.  
  
 **Commentaires**  
 Affiche le commentaire qui a été entré lorsque l'avertissement a été ignoré. Vous pouvez ajouter ou modifier un commentaire ici.  
  
 **Réactiver**  
 Réactive les avertissements sélectionnés.  
  
> [!NOTE]  
>  Si un objet a un avertissement mais que son état est non valide ou que cet objet a été supprimé manuellement du projet, une icône d'erreur apparaît à côté de l'avertissement dans la liste. Pour ignorer l’avertissement, sélectionnez-le, puis cliquez sur **Ignorer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue ignorer l’avertissement &#40;Analysis Services-données multidimensionnelles&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md)   
 [Concepteur de base de données &#40;général&#41; &#40;Analysis Services-données multidimensionnelles&#41;](general-database-designer-analysis-services-multidimensional-data.md)  
  
  
