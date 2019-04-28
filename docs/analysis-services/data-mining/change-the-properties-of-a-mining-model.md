---
title: Modifier les propriétés d’un modèle d’exploration de données | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a3650b284e8817c2b7f8aee6a0beca71c275d6a1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62670370"
---
# <a name="change-the-properties-of-a-mining-model"></a>Modifier les propriétés d'un modèle d'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Certaines propriétés du modèle d'exploration de données s'appliquent au modèle dans son ensemble, et d'autres propriétés de modèle s'appliquent à des colonnes individuelles. La propriété **Extraction** , qui spécifie si les données de cas doivent être disponibles pour l’interrogation, et la propriété **Description** sont des exemples de propriétés qui s’appliquent à l’ensemble du modèle. Les propriétés qui s’appliquent à la colonne sont **Utilisation** et **ModelingFlags**, qui contrôlent l’utilisation des données de la colonne dans le modèle.  
  
 Les propriétés de modèle suivantes ont des éditeurs avancés que vous pouvez utiliser pour créer des expressions ou pour configurer les propriétés de modèle complexes. Les propriétés suivantes fournissent :  
  
-   **Filtre** propriété : Ouvre le [Data Set filtre or Model filtre Dialog Box](http://msdn.microsoft.com/library/a9602174-b7e2-4e16-8ded-dfd8eb9264d7).  
  
-   **AlgorithmParameters** propriété : Ouvre le [boîte dialogue Paramètres d’algorithme &#40;affichage des modèles d’exploration de&#41;](http://msdn.microsoft.com/library/57f9f6f8-8ca4-4a6e-8f18-85f0571b7060).  
  
 Pour plus d’informations sur la définition des propriétés dans un modèle d’exploration, consultez [Colonnes de modèle d’exploration de données](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>Pour modifier les propriétés d'un modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit sur l’en-tête de colonne contenant le nom du modèle d’exploration de données ou sur la ligne de la grille qui contient le nom de l’algorithme d’exploration de données, puis sélectionnez **Propriétés**.  
  
2.  Dans la fenêtre **Propriétés** à droite de l’écran, mettez en surbrillance la valeur qui correspond à la propriété à modifier, puis entrez la nouvelle valeur.  
  
     La nouvelle valeur est appliquée lorsque vous sélectionnez un élément différent dans le concepteur.  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>Pour modifier les propriétés d'une colonne de modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit sur la cellule de la grille à l’intersection de la colonne de la structure d’exploration de données et du modèle d’exploration de données, puis sélectionnez **Propriétés**.  
  
2.  Dans la fenêtre **Propriétés** à droite de l’écran, mettez en surbrillance la valeur qui correspond à la propriété à modifier, puis entrez la nouvelle valeur.  
  
    > [!NOTE]  
    >  Si l’utilisation de la colonne est définie sur **Ignorer**, la fenêtre **Propriétés** pour la colonne est vide.  
  
     La nouvelle valeur est appliquée lorsque vous sélectionnez un élément différent dans le concepteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures des modèles d’exploration de données](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
