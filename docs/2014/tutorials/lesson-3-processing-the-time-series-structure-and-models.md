---
title: 'Leçon 3 : traitement de la structure et des modèles de série chronologique | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 493d27c9836eb765c655eba5bbb004e4d48cde40
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63042875"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>Leçon 3 : Traitement de la structure et des modèles de série chronologique
  Dans cette leçon, vous allez utiliser l’instruction [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) pour traiter les structures d’exploration de données de série chronologique et les modèles d’exploration de données que vous avez créés.  
  
 Lorsque vous traitez une structure d'exploration de données, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] lit les données sources et génère les structures qui soutiennent les modèles d'exploration de données. Vous devez toujours traiter un modèle et une structure d'exploration de données au moment où vous les créez. Si vous spécifiez la structure d'exploration de données lors de l'utilisation de l'instruction INSERT INTO, l'instruction traite la structure et tous ses modèles d'exploration de données associés.  
  
 Lorsque vous ajoutez un modèle d'exploration de données à une structure d'exploration de données déjà traitée, vous pouvez utiliser l'instruction `INSERT INTO MINING MODEL` pour traiter uniquement le nouveau modèle d'exploration de données à l'aide des données existantes.  
  
 Pour plus d’informations sur le traitement des modèles d’exploration de données, consultez [exigences et considérations relatives au traitement &#40;&#41;d’exploration de données ](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="insert-into-statement"></a>Instruction INSERT INTO  
 Pour effectuer l’apprentissage de la structure d’exploration de données de série chronologique et de tous ses modèles d’exploration de données associés, utilisez l’instruction [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) . Le code de cette instruction peut être divisé selon les sections suivantes :  
  
-   Identification de la structure d'exploration de données  
  
-   Liste des colonnes de la structure d'exploration de données  
  
-   Définition des données d'apprentissage  
  
 L'exemple générique suivant utilise l'instruction `INSERT INTO` :  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 La première ligne du code identifie la structure d'exploration de données à apprendre :  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Les lignes suivantes du code précisent les colonnes définies par la structure d'exploration de données. Vous devez répertorier chaque colonne dans la structure d'exploration de données et chaque colonne doit mapper une colonne figurant dans les données de la requête source.  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 Les dernières lignes du code précisent les données à utiliser pour l'apprentissage de la structure d'exploration de données.  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 Dans cette leçon, vous allez utiliser l'instruction `OPENQUERY` pour définir les données sources. Pour plus d’informations sur les autres méthodes de définition d’une requête sur les données sources, consultez [&#60;&#62;de requête de données source ](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Au cours de cette leçon, vous allez effectuer la tâche suivante :  
  
-   traiter la structure d'exploration de données Forecasting_MIXED_Structure ;  
  
-   traiter les modèles d'exploration de données associés Forecasting_MIXED, Forecasting_ARIMA et Forecasting_ARTXP.  
  
## <a name="processing-the-time-series-mining-structure"></a>Traitement de la structure d'exploration de données de série chronologique  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>Pour traiter la structure d'exploration de données et les modèles associés à l'aide d'une instruction INSERT INTO  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]droit sur l’instance de, pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction INSERT INTO dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    [<mining structure>]  
    ```  
  
     par :  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <mining structure columns>  
    ```  
  
     par :  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     par :  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     La requête source fait référence [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] à la source de données définie dans l’exemple de projet IntermediateTutorial. Elle utilise cette source de données pour accéder à la vue vTimeSeries. Cette vue renferme les données sources à utiliser pour l'apprentissage du modèle d'exploration de données. Si vous n’êtes pas familiarisé avec ce projet ou ces vues, consultez[leçon 2 : génération d’un scénario de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
7.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `ProcessForecastingAll.dmx`.  
  
8.  Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
 Une fois que l'exécution de la requête est terminée, vous pouvez créer des prédictions en utilisant les modèles d'exploration de données traités. Dans la leçon suivante, vous allez créer plusieurs prédictions basées sur les modèles d'exploration de données que vous avez créés.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 4 : Création de prédictions de série chronologique à l'aide d'extensions DMX](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exigences et considérations relatives au traitement &#40;l’exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#60;&#62;de requête de données source](/sql/dmx/source-data-query)   
 [&#41;&#40;DMX OPENQUERY](/sql/dmx/source-data-query-openquery)  
  
  
