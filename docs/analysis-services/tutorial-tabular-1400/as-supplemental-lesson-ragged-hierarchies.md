---
title: 'Analysis Services leçon supplémentaire du didacticiel : Hiérarchies déséquilibrées | Microsoft Docs'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 39f8bcc63b7e5344f70a6d4a3b6c44ae3e69e108
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685396"
---
# <a name="supplemental-lesson---ragged-hierarchies"></a>Leçon supplémentaire - Hiérarchies déséquilibrées

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon supplémentaire, vous résoudre un problème courant lorsque pivotement sur des hiérarchies qui contiennent des valeurs vides (membres) à différents niveaux. Par exemple, une organisation où un responsable hiérarchique a chefs de service et des non-cadres comme collaborateurs directs. Ou bien, hiérarchies géographiques composées des pays-région-ville, où certaines villes n’ont pas un état parent ou la Province, par exemple Washington D.C., cité du Vatican. Lorsqu’une hiérarchie possède des membres vides, elle descend souvent à des niveaux différents ou déséquilibrés.

![as-lesson-detail-ragged-hierarchies-table](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-table.png)

Les modèles tabulaires au niveau de compatibilité 1400 ont supplémentaires **masquer les membres** propriété pour les hiérarchies. Le **par défaut** paramètre suppose il n’y aucun membre vide à tout niveau. Le **masquer les membres vides** paramètre exclut les membres vides à partir de la hiérarchie lors de l’ajout à un rapport ou tableau croisé dynamique.  
  
Durée estimée pour effectuer cette leçon : **20 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
Cet article de leçon supplémentaire fait partie d’un didacticiel de modélisation tabulaire. Avant d’effectuer les tâches de cette leçon supplémentaire, vous devez avoir terminé toutes les leçons précédentes ou disposer d’un projet de modèle d’exemple Adventure Works Internet Sales terminé. 

Si vous avez créé le projet AW Internet Sales dans le cadre du didacticiel, votre modèle ne contient pas encore les données ou une hiérarchie déséquilibrée. Pour effectuer cette leçon supplémentaire, vous devez d’abord créer le problème en ajoutant des tables supplémentaires, créer des relations, des colonnes calculées, une mesure et une hiérarchie d’organisation. Cette partie prend environ 15 minutes. Ensuite, vous pouvez résoudre le problème en quelques minutes seulement.  

## <a name="add-tables-and-objects"></a>Ajouter des tables et objets
  
### <a name="to-add-new-tables-to-your-model"></a>Pour ajouter de nouvelles tables à votre modèle
  
1.  Dans l’Explorateur de modèles tabulaires, développez **des Sources de données**, puis cliquez sur votre connexion > **importer de nouvelles Tables**.
  
2.  Dans le navigateur, sélectionnez **DimEmployee** et **FactResellerSales**, puis cliquez sur **OK**.

3.  Dans l’éditeur de requête, cliquez sur **importation**

4.  Créer les éléments suivants [relations](../tutorial-tabular-1400/as-lesson-4-create-relationships.md):

    | tableau 1           | colonne       | Direction du filtre   | tableau 2     | colonne      | Actif |
    |-------------------|--------------|--------------------|-------------|-------------|--------|
    | FactResellerSales | OrderDateKey | Par défaut            | DimDate     | Date        | Oui    |
    | FactResellerSales | DueDate      | Par défaut            | DimDate     | Date        | Non     |
    | FactResellerSales | ShipDateKey  | Par défaut            | DimDate     | Date        | Non     |
    | FactResellerSales | ProductKey   | Par défaut            | DimProduct  | ProductKey  | Oui    |
    | FactResellerSales | EmployeeKey  | Pour les deux Tables | DimEmployee | EmployeeKey | Oui    |

5. Dans le **DimEmployee** table, créer les éléments suivants [des colonnes calculées](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md): 

    **Chemin d'accès** 
    ```
    =PATH([EmployeeKey],[ParentEmployeeKey])
    ```

    **FullName** 
    ```
    =[FirstName] & " " & [MiddleName] & " " & [LastName]
    ```

    **Level1** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],1,1)) 
    ```

    **Level2** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],2,1)) 
    ```

    **Level3** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],3,1)) 
    ```

    **Level4** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],4,1)) 
    ```

    **Level5** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],5,1)) 
    ```

6.  Dans le **DimEmployee** table, créez un [hiérarchie](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md) nommé **organisation**. Ajoutez l’ordre des colonnes suivantes : **Level1**, **Level2**, **Level3**, **Level4**, **Level5**.

7.  Dans le **FactResellerSales** table, créer les éléments suivants [mesure](../tutorial-tabular-1400/as-lesson-6-create-measures.md):

    ```
    ResellerTotalSales:=SUM([SalesAmount])
    ```

8.  Utilisez [analyser dans Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md) pour ouvrir Excel et créer automatiquement un tableau croisé dynamique.

9.  Dans **PivotTable Fields**, ajouter le **organisation** hiérarchie à partir de la **DimEmployee** table **lignes**et le  **ResellerTotalSales** à partir de la **FactResellerSales** table **valeurs**.

    ![as-lesson-detail-ragged-hierarchies-pivottable](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable.png)

    Comme vous pouvez le voir dans le tableau croisé dynamique, la hiérarchie affiche des lignes qui sont déséquilibrées. Il existe plusieurs lignes où les membres vides sont affichés.

## <a name="to-fix-the-ragged-hierarchy-by-setting-the-hide-members-property"></a>Pour corriger la hiérarchie déséquilibrée en définissant les masquer les membres de propriété

1.  Dans **Explorateur de modèles tabulaires**, développez **Tables** > **DimEmployee** > **hiérarchies**  >  **Organisation**.

2.  Dans **propriétés** > **masquer les membres**, sélectionnez **masquer les membres vides**. 

    ![as-lesson-detail-ragged-hierarchies-hidemembers](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-hidemembers.png)

3.  De retour dans Excel, actualisez le tableau croisé dynamique. 

    ![as-lesson-detail-ragged-hierarchies-pivottable-refresh](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable-refresh.png)

    Voilà qui est beaucoup mieux !

## <a name="see-also"></a>Voir aussi   
[Leçon 9 : Créer des hiérarchies](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)  
[Leçon supplémentaire – sécurité dynamique](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Leçon supplémentaire – lignes de détails](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)  
