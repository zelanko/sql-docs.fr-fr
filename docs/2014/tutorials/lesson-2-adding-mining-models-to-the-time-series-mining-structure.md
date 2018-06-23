---
title: 'Leçon 2 : Ajout des modèles d’exploration de données à la Structure d’exploration de données de série chronologique | Documents Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75c2a74b-21ce-44fb-a26b-68be4c685c12
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cee3d839ae7a7bcce62c8a3a1d2f7cb62b1155e2
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312487"
---
# <a name="lesson-2-adding-mining-models-to-the-time-series-mining-structure"></a>Leçon 2 : Ajout de modèles d'exploration de données à la structure d'exploration de données de série chronologique
  Dans cette leçon, vous allez ajouter un nouveau modèle d’exploration de données à la structure d’exploration de données que vous venez de créer dans [leçon 1 : création d’un modèle d’exploration de données de série chronologique et la Structure d’exploration de](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md).  
  
## <a name="alter-mining-structure-statement"></a>Instruction ALTER MINING STRUCTURE  
 Pour ajouter un nouveau modèle d’exploration de données à une structure d’exploration de données existante, vous devez utiliser la [ALTER MINING STRUCTURE &#40;DMX&#41;] (instruction (~/dmx/alter-mining-structure-dmx.md). Le code dans l’instruction peut être classée dans les sections suivantes :  
  
-   Identification de la structure d'exploration de données  
  
-   Attribution d'un nom au modèle d'exploration de données  
  
-   Définition de la colonne clé  
  
-   Définition des colonnes prédictibles  
  
-   Spécification des modifications d'algorithme et de paramètre  
  
 L'exemple générique suivant utilise l'instruction ALTER MINING STRUCTURE :  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
   ([<key columns>],  
    <mining model columns>  
   )  
USING <algorithm name>([<algorithm parameters>])  
[WITH DRILLTHROUGH]  
```  
  
 La première ligne du code identifie la structure d'exploration de données existante à laquelle les modèles d'exploration de données seront ajoutés :  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 La ligne suivante du code désigne le modèle d'exploration de données qui sera ajouté à la structure d'exploration de données :  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 Pour plus d’informations sur l’appellation d’un objet dans DMX, consultez [identificateurs &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 Les lignes suivantes du code définissent les colonnes de la structure d'exploration de données employées dans le modèle d'exploration de données :  
  
```  
[<key columns>],  
<mining model columns>  
```  
  
 Vous pouvez uniquement utiliser les colonnes déjà existantes dans la structure d'exploration de données ; de même, la première colonne de la liste doit correspondre à la colonne clé issue de la structure d'exploration de données.  
  
 Les lignes suivantes du code définissent l'algorithme d'exploration de données qui génère le modèle d'exploration de données et les paramètres d'algorithme que vous pouvez définir sur l'algorithme, puis indiquent si vous pouvez effectuer une extraction du modèle d'exploration de données vers des données détaillées de la vue dans les cas d'apprentissage :  
  
```  
USING <algorithm name>([<algorithm parameters>])  
WITH DRILLTHROUGH  
```  
  
 Pour plus d’informations sur les paramètres d’algorithme que vous pouvez régler, consultez [Microsoft Time Series algorithme Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md).  
  
 Vous pouvez spécifier l'utilisation d'une colonne du modèle d'exploration de données à des fins de prédiction en utilisant la syntaxe suivante :  
  
```  
<mining model column> PREDICT  
```  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Vous allez effectuer les tâches suivantes dans cette leçon :  
  
-   ajouter un nouveau modèle d'exploration de données de série chronologique à la structure ;  
  
-   modifier les paramètres d'algorithme pour utiliser une autre méthode d'analyse et de prédiction.  
  
## <a name="adding-an-arima-time-series-model-to-the-structure"></a>Ajout d'un modèle de série chronologique ARIMA à la structure  
 La première étape consiste à ajouter un nouveau modèle d'exploration de données de prévision à la structure existante. Par défaut, l'algorithme MTS ([!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series) crée des modèles d'exploration de données de série chronologique en utilisant deux algorithmes, ARIMA et ARTXP, puis en fusionnant les résultats. Toutefois, vous pouvez spécifier un seul algorithme à utiliser ou spécifier la fusion exacte des algorithmes. Au cours de cette étape, vous allez ajouter un nouveau modèle qui utilise uniquement l'algorithme ARIMA. Cet algorithme est optimisé pour les prédictions à long terme.  
  
#### <a name="to-add-an-arima-time-series-mining-model"></a>Pour ajouter un modèle d'exploration de données de série chronologique ARIMA  
  
1.  Dans **l’Explorateur d’objets**, cliquez sur l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pointez sur **nouvelle requête**, puis cliquez sur **DMX** pour ouvrir l’éditeur de requête et une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction ALTER MINING STRUCTURE dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <mining structure name>   
    ```  
  
     par :  
  
    ```  
    [Forecasting_MIXED_Structure]  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <mining model name>   
    ```  
  
     par :  
  
    ```  
    Forecasting_ARIMA  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    <key columns>,  
    ```  
  
     par :  
  
    ```  
    [ReportingDate],  
    [ModelRegion]  
    ```  
  
     Notez que vous n'avez pas besoin de répéter les informations relatives au type de date ou de contenu que vous avez fournies dans l'instruction CREATE MINING MODEL, parce que ces informations sont déjà stockées dans la structure d'exploration de données.  
  
6.  Remplacez le code suivant :  
  
    ```  
    <mining model columns>  
    ```  
  
     par :  
  
    ```  
    ([Quantity] PREDICT,  
    [Amount] PREDICT  
    )  
    ```  
  
7.  Remplacez le code suivant :  
  
    ```  
    USING <algorithm name>([<algorithm parameters>])   
    [WITH DRILLTHROUGH]  
    ```  
  
     par :  
  
    ```  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
     L'instruction obtenue doit se présenter comme suit :  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARIMA]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
8.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
9. Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Forecasting_ARIMA.dmx`.  
  
10. Dans la barre d’outils, cliquez sur le **Execute** bouton.  
  
## <a name="adding-an-artxp-time-series-model-to-the-structure"></a>Ajout d'un modèle de série chronologique ARTXP à la structure  
 L'algorithme ARTXP était l'algorithme de série chronologique par défaut dans SQL Server 2005 et il est optimisé pour des prédictions à court terme. Pour comparer des prédictions à l'aide des trois algorithmes de série chronologique, vous allez ajouter un autre modèle basé sur l'algorithme ARTXP.  
  
#### <a name="to-add-an-artxp-time-series-mining-model"></a>Pour ajouter un modèle d'exploration de données de série chronologique ARTXP  
  
1.  Copiez le code suivant dans une fenêtre de requête vide.  
  
     Notez que vous n'avez pas besoin d'apporter de modifications  l'exception du nom du nouveau modèle d'exploration de données et de la valeur du paramètre FORECAST_METHOD.  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARTXP]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARTXP')  
    WITH DRILLTHROUGH  
    ```  
  
2.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
3.  Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Forecasting_ARTXP.dmx`.  
  
4.  Dans la barre d’outils, cliquez sur le **Execute** bouton.  
  
 Dans la leçon suivante, vous allez traiter tous les modèles et la structure d'exploration de données.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 3 : Traitement de la série chronologique Structure et des modèles](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme de série chronologique de Microsoft](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Informations techniques de référence sur l’algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
