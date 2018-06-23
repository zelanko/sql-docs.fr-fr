---
title: Avertissements (Concepteur de base de données) (Analysis Services - données multidimensionnelles) | Documents Microsoft
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
- sql12.asvs.databasedesigner.warnings.f1
ms.assetid: 13f58b4d-f345-4fbc-ae2d-b3c8290a797d
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e00890be8fac0fb97f0887034d5c7b04c049ebd0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051792"
---
# <a name="warnings-database-designer-analysis-services---multidimensional-data"></a>Avertissements (Concepteur de bases de données) (Analysis Services - Données multidimensionnelles)
  L’onglet **Avertissements** permet d’afficher et d’ignorer des règles globalement, et d’afficher et de réactiver des instances spécifiques d’avertissements ignorés. L'onglet **Avertissements** affiche deux grilles : **Règles d'avertissements de conception** et **Avertissements ignorés**.  
  
 **Pour afficher l’onglet avertissements**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
2.  Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur **Modifier la base de données**, puis sur l’onglet **Avertissements** .  
  
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
  
 **Objet**  
 Affiche une icône qui représente le type d'objet et le nom d'objet.  
  
 **Type**  
 Affiche le type d'objet.  
  
 **Description**  
 Affiche le nom de la règle.  
  
 **Importance**  
 Affiche l'importance affectée à la règle.  
  
 **Commentaires**  
 Affiche le commentaire qui a été entré lorsque l'avertissement a été ignoré. Vous pouvez ajouter ou modifier un commentaire ici.  
  
 **Activer de nouveau**  
 Réactive les avertissements sélectionnés.  
  
> [!NOTE]  
>  Si un objet a un avertissement mais que son état est non valide ou que cet objet a été supprimé manuellement du projet, une icône d'erreur apparaît à côté de l'avertissement dans la liste. Pour ignorer l’avertissement, sélectionnez-le, puis cliquez sur **Ignorer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fermer la boîte de dialogue d’avertissement &#40;Analysis Services - données multidimensionnelles&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md)   
 [Général &#40;Concepteur de base de données&#41; &#40;Analysis Services - données multidimensionnelles&#41;](general-database-designer-analysis-services-multidimensional-data.md)  
  
  