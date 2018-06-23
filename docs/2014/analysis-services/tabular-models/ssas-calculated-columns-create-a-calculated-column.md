---
title: Créer une colonne calculée (SSAS tabulaire) | Documents Microsoft
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
- sql12.as.daxref.CreataCalculatedColumn.f1
ms.assetid: 59440510-2d76-41dc-9b55-edc15259f9da
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fc966ebf8dd9fcb88bc6ef8ad6cad4d44c044d00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052709"
---
# <a name="create-a-calculated-column-ssas-tabular"></a>Créer une colonne calculée (SSAS Tabulaire)
  Les colonnes calculées permettent d'ajouter de nouvelles données à votre modèle. Au lieu de coller ou importer des valeurs dans la colonne, vous créez une formule DAX qui définit les valeurs de niveau de ligne de la colonne. Les valeurs de chaque ligne d'une colonne calculée sont calculées et remplies lorsque vous créez une formule non valide puis cliquez sur ENTRÉE. La colonne calculée peut ensuite être ajoutée à une application de création de rapports ou d'analyse, comme toute autre colonne de données. Cette rubrique décrit comment créer une nouvelle colonne calculée à l'aide de la barre de formule DAX dans le générateur de modèles.  
  
#### <a name="to-create-a-new-calculated-column"></a>Pour créer une nouvelle colonne calculée  
  
1.  Dans le générateur de modèles, dans la vue de données, sélectionnez la table à laquelle vous souhaitez ajouter une colonne calculée, cliquez sur le menu **Colonne** , puis sur **Ajouter une colonne**.  
  
     **Ajouter une colonne** est mis en surbrillance dans la colonne la plus à droite vide, et le curseur se place dans la barre de formule.  
  
     Pour intercaler une colonne entre deux colonnes existantes, cliquez avec le bouton droit sur une colonne existante, puis sélectionnez **Insérer une colonne**.  
  
2.  Dans la barre de formule, effectuez l'une des opérations suivantes :  
  
    -   Tapez un signe égal suivi d'une formule.  
  
    -   Tapez un signe égal, suivi d'une fonction DAX, d'arguments et de paramètres, comme requis par la fonction.  
  
    -   Cliquez sur le bouton de fonction (**fx**) puis, dans la boîte de dialogue **Insérer une fonction** , sélectionnez une catégorie et une fonction, puis cliquez sur **OK**. Dans la barre de formule, tapez les arguments et les paramètres restants, comme requis par la fonction.  
  
3.  Appuyez sur Entrée pour accepter la formule.  
  
     La formule remplit la colonne tout entière et une valeur est calculée pour chaque ligne.  
  
> [!TIP]  
>  Vous pouvez utiliser la saisie semi-automatique des formules DAX au milieu d'une formule existante avec les fonctions imbriquées. Le texte immédiatement avant le point d'insertion est utilisé pour afficher des valeurs dans la liste déroulante, et tout le texte après le point d'insertion reste inchangé.  
  
## <a name="see-also"></a>Voir aussi  
 [Colonnes calculées &#40;SSAS tabulaire&#41;](ssas-calculated-columns.md)   
 [Mesures &#40;SSAS tabulaire&#41;](measures-ssas-tabular.md)  
  
  