---
title: 'Leçon 1 : Création d’une série chronologique de modèle d’exploration de données et la Structure d’exploration de données | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b201f2b8-9ab5-425b-9ff3-fe321a60a7b7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2513bc3837dd224f6561eb0015ced538ea3add8c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62678450"
---
# <a name="lesson-1-creating-a-time-series-mining-model-and-mining-structure"></a>Leçon 1 : Création d’une structure d’exploration de données et de modèle d’exploration de données de série chronologique
  Dans cette leçon, vous allez créer un modèle d'exploration de données qui vous permet de prédire des valeurs dans le temps à partir de données historiques. Lorsque vous créez le modèle, la structure sous-jacente est générée automatiquement et peut servir de base pour les modèles d'exploration de données supplémentaires.  
  
 Cette leçon suppose que vous connaissez les modèles de prévision et les spécifications de l'algorithme MTS (Microsoft Time Series). Pour plus d’informations, consultez [Algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md).  
  
## <a name="create-mining-model-statement"></a>Instruction CREATE MINING MODEL  
 Pour créer un modèle d’exploration de données directement et générer automatiquement la structure d’exploration de données sous-jacente, vous utilisez le [CREATE MINING MODEL &#40;DMX&#41; ](/sql/dmx/create-mining-model-dmx) instruction. Le code dans l’instruction peut être divisé en parties suivantes :  
  
-   Attribution d'un nom au modèle  
  
-   Définition de l'horodatage  
  
-   Définition de la colonne clé de série facultative  
  
-   Définition des attributs ou de l'attribut prédictible  
  
 L'exemple générique suivant utilise l'instruction CREATE MINING MODEL :  
  
```  
CREATE MINING MODEL [<Mining Structure Name>]  
(  
   <key columns>,  
   <predictable attribute columns>  
)  
USING <algorithm name>([parameter list])  
WITH DRILLTHROUGH  
```  
  
 La première ligne du code définit le nom du modèle d'exploration de données :  
  
```  
CREATE MINING MODEL [Mining Model Name]  
```  
  
 Le service Analysis Services génère un nom pour la structure sous-jacente en annexant "_structure" au nom du modèle, ce qui garantit l'unicité du nom de la structure dans le nom du modèle. Pour plus d’informations sur l’appellation d’un objet dans DMX, consultez [identificateurs &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 La ligne suivante du code définit la colonne clé pour le modèle d'exploration de données qui dans le cas d'un modèle de série chronologique identifie de manière unique une étape dans les données sources. L’étape est identifié par le `KEY TIME` mots clés après les types de données et le nom de colonne. Si le modèle de série chronologique a une clé de série séparée, il est identifié à l'aide du mot clé `KEY`.  
  
```  
<key columns>  
```  
  
 La ligne suivante du code est utilisée pour définir les colonnes du modèle qui sera prédit. Vous pouvez avoir plusieurs attributs prédictibles dans un modèle d'exploration de données unique. Lorsqu'il y a plusieurs attributs prédictibles, l'algorithme MTS (Microsoft Time Series) génère une analyse séparée pour chaque série :  
  
```  
<predictable attribute columns>  
```  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Vous allez effectuer les tâches suivantes dans cette leçon :  
  
-   créer une requête vide ;  
  
-   modifier la requête pour créer le modèle d'exploration de données ;  
  
-   exécuter la requête.  
  
## <a name="creating-the-query"></a>Création de la requête  
 La première étape consiste à se connecter à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et à créer une nouvelle requête DMX dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>Pour créer une requête DMX dans SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Dans le **se connecter au serveur** boîte de dialogue pour **type de serveur**, sélectionnez **Analysis Services**. Dans **nom du serveur**, type `LocalHost`, ou le nom de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que vous souhaitez vous connecter à pour cette leçon. Cliquer sur **Se connecter**.  
  
3.  Dans **Explorateur d’objets**, avec le bouton droit de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
## <a name="altering-the-query"></a>Modification de la requête  
 L'étape suivante consiste à modifier l'instruction CREATE MINING MODEL pour créer le modèle d'exploration de données utilisé pour la prévision ainsi que sa structure d'exploration de données sous-jacente.  
  
#### <a name="to-customize-the-create-mining-model-statement"></a>Pour personnaliser l'instruction CREATE MINING MODEL  
  
1.  Dans l'Éditeur de requête, copiez l'exemple générique de l'instruction CREATE MINING MODEL dans la requête vide.  
  
2.  Remplacez le code suivant :  
  
    ```  
    [mining model name]   
    ```  
  
     par :  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
3.  Remplacez le code suivant :  
  
    ```  
    <key columns>  
    ```  
  
     par :  
  
    ```  
    [Reporting Date] DATE KEY TIME,  
    [Model Region] TEXT KEY  
    ```  
  
     Le mot clé `TIME KEY` indique que la colonne ReportingDate contient les valeurs de l'étape utilisées pour classer les valeurs. Les étapes peuvent être des dates et des heures, des entiers ou tout type de données classées, à condition que les valeurs soient uniques et les données triées.  
  
     Les mots clés `TEXT` et `KEY` indiquent que la colonne ModelRegion contient une clé de série supplémentaire. Vous ne pouvez avoir qu'une seule clé de série, et les valeurs dans la colonne doivent être distinctes.  
  
4.  Remplacez le code suivant :  
  
    ```  
    < predictable attribute columns> )  
    ```  
  
     par :  
  
    ```  
    [Quantity] LONG CONTINUOUS PREDICT,  
    [Amount] DOUBLE CONTINUOUS PREDICT  
    )  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    USING <algorithm name>([parameter list])  
    WITH DRILLTHROUGH  
    ```  
  
     par :  
  
    ```  
    USING Microsoft_Time_Series(AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
    ```  
  
     Le paramètre d'algorithme, `AUTO_DETECT_PERIODICITY` = 0.8, indique que vous souhaitez que l'algorithme détecte des cycles dans les données. Définir cette valeur proche de 1 privilégie la découverte de nombreux modèles mais peut ralentir le traitement.  
  
     Le paramètre d'algorithme, `FORECAST_METHOD`, indique si vous souhaitez que les données soient analysées à l'aide de ARTXP, ARIMA, ou un mélange des deux.  
  
     Le mot clé, `WITH DRILLTHROUGH`, spécifie que vous souhaitez consulter des statistiques détaillées dans les données sources une fois le modèle terminé. Vous devez ajouter cette clause pour parcourir le modèle à l'aide de la Visionneuse de l'algorithme MTS (Microsoft Time Series). Elle n'est pas obligatoire pour la prédiction.  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    CREATE MINING MODEL [Forecasting_MIXED]  
         (  
        [Reporting Date] DATE KEY TIME,  
        [Model Region] TEXT KEY,  
        [Quantity] LONG CONTINUOUS PREDICT,  
        [Amount] DOUBLE CONTINUOUS PREDICT  
        )  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
  
    ```  
  
6.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
7.  Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Forecasting_MIXED.dmx`.  
  
## <a name="executing-the-query"></a>L’exécution de la requête  
 La dernière étape concerne l'exécution de la requête. Après sa création et son enregistrement, la requête doit être exécutée pour permettre la création sur le serveur de sa structure d'exploration de données et du modèle d'exploration de données. Pour plus d’informations sur l’exécution de requêtes dans l’éditeur de requête, consultez [éditeur de requête du moteur de base de données &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>Pour exécuter la requête  
  
-   Dans l’éditeur de requête, dans la barre d’outils, cliquez sur **Execute**.  
  
     L’état de la requête est affiché dans le **Messages** onglet en bas de l’éditeur de requête une fois l’instruction terminée l’exécution. Les messages doivent révéler le texte suivant :  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Une nouvelle structure appelée **Forecasting_MIXED_Structure** existe maintenant sur le serveur, ainsi que le modèle d’exploration de données connexes **Forecasting_MIXED**.  
  
 Dans la leçon suivante, vous allez ajouter un modèle d’exploration de données pour le **Forecasting_MIXED** structure d’exploration de données que vous venez de créer.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Ajout de modèles d’exploration de données à la Structure d’exploration de données de série chronologique](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu du modèle pour les modèles de série chronologique d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)   
 [Informations techniques de référence sur l’algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
