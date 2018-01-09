---
title: "Importer des données à l’aide d’une requête native (Analysis Services) | Documents Microsoft"
ms.custom: 
ms.date: 10/26/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b1200775d4b80639c3e6e2cb5ab127e3d1bb5254
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="import-data-by-using-a-native-query"></a>Importer des données à l’aide d’une requête native
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Pour les modèles tabulaires 1400, la nouvelle expérience d’obtenir des données dans les projets Visual Studio Analysis Services fournit une flexibilité considérable dans la manière dont vous pouvez combiner vos données pendant l’importation. Cet article décrit la création d’une connexion à une source de données et puis en créant une requête SQL native pour spécifier l’importation de données.

Afin d’effectuer les tâches décrites dans cet article, assurez-vous que vous utilisez la version la plus récente de SSDT. Si vous utilisez Visual Studio 2017, assurez-vous que vous avez téléchargé et installé le 2017 septembre ou version ultérieure Microsoft Analysis Services projets VSIX.

[Téléchargez et installez SSDT](../../ssdt/download-sql-server-data-tools-ssdt.md)

[Télécharger Microsoft Analysis Services projet VSIX](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)

## <a name="create-a-datasource-connection"></a>Créer une connexion de source de données
Si vous ne disposez pas d’une connexion à votre source de données, vous devez en créer un.

1. Dans Visual Studio > **l’Explorateur de modèles tabulaires**, avec le bouton droit **des Sources de données**, puis cliquez sur **nouvelle Source de données**.
2. Dans **obtenir des données**, sélectionnez votre type de source de données, puis cliquez sur **connexion**. Suivez les étapes supplémentaires requises pour se connecter à votre source de données.


## <a name="enter-a-query-as-a-named-expression"></a>Entrez une requête sous la forme d’une expression nommée
1. Dans **l’Explorateur de modèles tabulaires**, avec le bouton droit **Expressions** > **modifier les Expressions**.
2. Dans **l’éditeur de requête**, cliquez sur **requête** > **nouvelle requête** > **requête vide**
3. Dans la barre de formule, tapez
    ```
    = Value.NativeQuery(#"DATA SOURCE NAME", "SELECT * FROM …")
    ```
4. Pour créer une table, dans **requêtes**, avec le bouton droit de la requête, puis sélectionnez **créer une Table**. La nouvelle table aura le même nom que la requête.


## <a name="example"></a> Exemple
Cette requête native crée une table d’employés dans le modèle qui inclut toutes les colonnes de la table de Dimension.Employee à la source de données.

```
= Value.NativeQuery(#"SQL/myserver;WideWorldImportersDW", "SELECT * FROM Dimension.Employee")
```
![Éditeur de requête](media/ssas-import-query-example.png)


Après l’importation, une table nommée Employees est créée dans le modèle.   

![Éditeur de requête](media/ssas-import-query-example-table.png)


## <a name="see-also"></a>Voir aussi  
 [Value.NativeQuery](https://msdn.microsoft.com/library/mt736917.aspx)   
 [Emprunt d’identité](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)   

  
