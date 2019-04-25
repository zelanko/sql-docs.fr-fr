---
title: Importer des données à l’aide d’une requête native (Analysis Services) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 67466abfccb03a689d5f717159e833143fcfafb4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472044"
---
# <a name="import-data-by-using-a-native-query"></a>Importer des données à l’aide d’une requête native
[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]
Pour les modèles tabulaires 1400, la nouvelle expérience d’obtenir des données dans les projets Visual Studio Analysis Services fournit une flexibilité considérable dans la façon dont vous permet de regrouper vos données pendant l’importation. Cet article décrit la création d’une connexion à une source de données, puis en créant une requête SQL native pour spécifier l’importation de données.

Pour pouvoir effectuer les tâches décrites dans cet article, vérifiez que vous utilisez la dernière version de SSDT. Si vous utilisez Visual Studio 2017, assurez-vous que vous avez téléchargé et installé le septembre 2017 ou version ultérieure Microsoft Analysis Services projets VSIX.

[Télécharger et installer SSDT](../../ssdt/download-sql-server-data-tools-ssdt.md)

[Télécharger Microsoft Analysis Services projets VSIX](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)

## <a name="create-a-datasource-connection"></a>Créer une connexion de source de données
Si vous ne disposez pas d’une connexion à votre source de données, vous devez en créer un.

1. Dans Visual Studio > **Explorateur de modèles tabulaires**, avec le bouton droit **des Sources de données**, puis cliquez sur **nouvelle Source de données**.
2. Dans **obtenir des données**, sélectionnez votre type de source de données, puis cliquez sur **Connect**. Suivez les étapes supplémentaires requises pour se connecter à votre source de données.


## <a name="enter-a-query-as-a-named-expression"></a>Entrez une requête comme une expression nommée
1. Dans **Explorateur de modèles tabulaires**, avec le bouton droit **Expressions** > **modifier les Expressions**.
2. Dans **éditeur de requête**, cliquez sur **requête** > **nouvelle requête** > **requête vide**
3. Dans la barre de formule, tapez
    ```
    = Value.NativeQuery(#"DATA SOURCE NAME", "SELECT * FROM ...")
    ```
4. Pour créer une table, dans **requêtes**, avec le bouton droit de la requête, puis sélectionnez **créer une Table**. La nouvelle table aura le même nom que la requête.


## <a name="example"></a>Exemple
Cette requête native crée une table d’employés dans le modèle qui inclut toutes les colonnes de la table de Dimension.Employee à la source de données.

```
= Value.NativeQuery(#"SQL/myserver;WideWorldImportersDW", "SELECT * FROM Dimension.Employee")
```
![Éditeur de requête](media/ssas-import-query-example.png)


Après avoir importé, une table nommée Employees est créée dans le modèle.   

![Éditeur de requête](media/ssas-import-query-example-table.png)


## <a name="see-also"></a>Voir aussi  
 [Value.NativeQuery](https://msdn.microsoft.com/library/mt736917.aspx)   
 [Emprunt d’identité](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)   

  
