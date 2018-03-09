---
title: "Programmation des objets d’exploration de données AMO | Documents Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- programming [AMO]
- data mining [AMO]
- AMO, data mining
- Analysis Management Objects, data mining
ms.assetid: d27f58b9-91be-449c-8403-439aa6dd1ff9
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: be27072d93bb9cee3d787732e57fc591452c2191
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="programming-amo-data-mining-objects"></a>Programmation d'objets d'exploration de données AMO
  La programmation d'objets d'exploration de données à l'aide d'AMO est simple et directe. La première étape consiste à créer le modèle de structure de données pour prendre en charge le projet d'exploration de données. Vous devez ensuite créer le modèle d'exploration de données qui prend en charge l'algorithme d'exploration de données que vous souhaitez utiliser pour prédire ou rechercher les relations invisibles sur lesquelles reposent vos données. Dès lors que le projet d'exploration de données est créé (y compris la structure et les algorithmes), vous pouvez traiter les modèles d'exploration de données pour obtenir les modèles ayant fait l'objet d'un apprentissage que vous utiliserez par la suite lors des interrogations et des prédictions réalisées à partir de l'application cliente.  
  
 L'un des points à retenir est qu'AMO n'a pas été conçu pour interroger ; AMO a pour objet de gérer et administrer vos structures et modèles d'exploration de données. Pour interroger vos données, utilisez [développement avec ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md).  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Objets MiningStructure](#MiningStructure)  
  
-   [Objets MiningModel](#MiningModel)  
  
##  <a name="MiningStructure">Objets MiningStructure</a>  
 Une structure d'exploration de données correspond à la définition de la structure de données utilisée pour créer tous les modèles d'exploration de données. Une structure d'exploration de données contient une liaison à une vue de source de données définie dans la base de données et contient des définitions pour toutes les colonnes participant aux modèles d'exploration de données. Une structure d’exploration de données peut avoir plusieurs modèles d’exploration de données.  
  
 La création d'un objet <xref:Microsoft.AnalysisServices.MiningStructure> passe par les étapes suivantes :  
  
1.  Créez l'objet <xref:Microsoft.AnalysisServices.MiningStructure> et remplissez les attributs de base. Les attributs de base se composent notamment du nom d'objet, de l'ID d'objet (identification interne) et de la liaison de source de données.  
  
2.  Créez les colonnes du modèle. Les colonnes peuvent être des définitions scalaires ou de table.  
  
     Chaque colonne a besoin d'un nom et d'un ID interne, d'un type, d'une définition de contenu et d'une liaison.  
  
3.  Mettez à jour l'objet <xref:Microsoft.AnalysisServices.MiningStructure> sur le serveur en utilisant la méthode Update de l'objet.  
  
     Il est possible de traiter les structures d'exploration de données. À cette occasion, les modèles d'exploration de données enfants sont traités ou font l'objet d'un nouvel apprentissage.  
  
 L'exemple de code suivant crée une structure d'exploration de données pour prévoir les ventes dans une série chronologique. Avant d’exécuter l’exemple de code, assurez-vous que la base de données *db*, passé comme paramètre pour `CreateSalesForecastingMiningStructure`, contient dans `db.DataSourceViews[0]` une référence à la vue *dbo.vTimeSeries* dans les [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] base de données exemple.  
  
```  
public static MiningStructure CreateSalesForecastingMiningStructure(Database db)  
{  
    MiningStructure ms = db.MiningStructures.FindByName("Forecasting Sales Structure");  
    if (ms != null)  
        ms.Drop();  
    ms = db.MiningStructures.Add("Forecasting Sales Structure", "Forecasting Sales Structure");  
    ms.Source = new DataSourceViewBinding(db.DataSourceViews[0].ID);  
  
    ScalarMiningStructureColumn amount = ms.Columns.Add("Amount", "Amount");  
    amount.Type = MiningStructureColumnTypes.Double;  
    amount.Content = MiningStructureColumnContents.Continuous;  
    amount.KeyColumns.Add("vTimeSeries", "Amount", OleDbType.Currency);  
  
    ScalarMiningStructureColumn modelRegion = ms.Columns.Add("Model Region", "Model Region");  
    modelRegion.IsKey = true;  
    modelRegion.Type = MiningStructureColumnTypes.Text;  
    modelRegion.Content = MiningStructureColumnContents.Key;  
    modelRegion.KeyColumns.Add("vTimeSeries", "ModelRegion", OleDbType.WChar, 56);  
  
    ScalarMiningStructureColumn qty = ms.Columns.Add("Quantity", "Quantity");  
    qty.Type = MiningStructureColumnTypes.Long;  
    qty.Content = MiningStructureColumnContents.Continuous;  
    qty.KeyColumns.Add("vTimeSeries", "Quantity", OleDbType.Integer);  
  
    ScalarMiningStructureColumn timeIndex = ms.Columns.Add("TimeIndex", "TimeIndex");  
    timeIndex.IsKey = true;  
    timeIndex.Type = MiningStructureColumnTypes.Long;  
    timeIndex.Content = MiningStructureColumnContents.KeyTime;  
    timeIndex.KeyColumns.Add("vTimeSeries", "TimeIndex", OleDbType.Integer);  
  
    ms.Update();  
    return ms;  
}  
```  
  
##  <a name="MiningModel">Objets MiningModel</a>  
 Un modèle d'exploration de données est une base de données de référentiel pour toutes les colonnes et définitions de colonne vouées à être utilisées dans un algorithme d'exploration de données.  
  
 La création d'un objet <xref:Microsoft.AnalysisServices.MiningModel> passe par les étapes suivantes :  
  
1.  Créez l'objet <xref:Microsoft.AnalysisServices.MiningModel> et remplissez les attributs de base.  
  
     Les attributs de base se composent d'un nom d'objet, d'un ID d'objet (identification interne) et d'une spécification d'algorithme d'exploration de données.  
  
2.  Ajoutez les colonnes du modèle d'exploration de données. L'une des colonnes doit être définie comme clé de cas.  
  
3.  Mettez à jour l'objet <xref:Microsoft.AnalysisServices.MiningModel> sur le serveur en utilisant la méthode Update de l'objet.  
  
     Les objets <xref:Microsoft.AnalysisServices.MiningModel> peuvent être traités indépendamment des autres modèles de l'objet <xref:Microsoft.AnalysisServices.MiningStructure> parent.  
  
 L'exemple de code suivant crée un modèle de prévision Microsoft Time Series basé sur la structure d'exploration de données « Forecasting Sales Structure » :  
  
```  
public static MiningModel CreateSalesForecastingMiningModel(MiningStructure ms)  
{  
    if (ms.MiningModels.ContainsName("Sales Forecasting Model"))  
    {  
        ms.MiningModels["Sales Forecasting Model"].Drop();  
    }  
    MiningModel mm = ms.CreateMiningModel(true, "Sales Forecasting Model");  
    mm.Algorithm = MiningModelAlgorithms.MicrosoftTimeSeries;  
    mm.AlgorithmParameters.Add("PERIODICITY_HINT", "{12}");  
  
    MiningModelColumn amount = new MiningModelColumn();  
    amount.SourceColumnID = "Amount";  
    amount.Usage = MiningModelColumnUsages.Predict;  
  
    MiningModelColumn modelRegion = new MiningModelColumn();  
    modelRegion.SourceColumnID = "Model Region";  
    modelRegion.Usage = MiningModelColumnUsages.Key;  
  
    MiningModelColumn qty = new MiningModelColumn();  
    qty.SourceColumnID = "Quantity";  
    qty.Usage = MiningModelColumnUsages.Predict;  
  
    MiningModelColumn ti = new MiningModelColumn();  
    ti.SourceColumnID = "TimeIndex";  
    ti.Usage = MiningModelColumnUsages.Key;  
  
    mm.Update();  
    mm.Process(ProcessType.ProcessFull);  
    return mm;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices>   
 [Classes fondamentales AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)   
 [Présentation des Classes AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Classes d’exploration de données AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-data-mining-classes.md)   
 [Architecture logique &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Les objets de base de données &#40; Analysis Services - données multidimensionnelles &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
