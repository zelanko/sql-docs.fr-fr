---
title: 'Leçon 3 : Traitement de la Structure d’exploration de données Bike Buyer | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e3f85016b32884b9a6b809e28d20d9985f97cd9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62655802"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a>Leçon 3 : Traitement de la structure d’exploration de données Bike Buyer
  Dans cette leçon, vous allez utiliser l’insertion dans l’instruction et la vue vTargetMail de la [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] base de données exemple pour traiter les structures d’exploration de données et les modèles d’exploration de données que vous avez créé dans [leçon 1 : Création de la Structure d’exploration de données Bike Buyer](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) et [leçon 2 : Ajout des modèles d’exploration de données à la Structure d’exploration de données Bike Buyer](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).  
  
 Lorsque vous traitez une structure d'exploration de données, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] lit les données sources et génère les structures qui soutiennent les modèles d'exploration de données. Lorsque vous traitez un modèle d'exploration de données, les données définies par la structure sont transmises via l'algorithme d'exploration de données de votre choix. L'algorithme recherche des tendances et des modèles, puis stocke les informations recueillies dans le modèle d'exploration de données. Par conséquent, le modèle d'exploration de données ne contient pas les données source réelles mais plutôt les informations recueillies par l'algorithme. Pour plus d’informations sur les modèles d’exploration de données de traitement, consultez [traitement des exigences et considérations &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Si vous modifiez une colonne de structure ou les données sources, vous devez simplement retraiter la structure d'exploration de données. Si vous ajoutez un modèle d'exploration de données à une structure d'exploration de données déjà traitée, vous pouvez utiliser l'instruction INSERT INTO MINING MODEL pour effectuer l'apprentissage du nouveau modèle d'exploration de données.  
  
## <a name="train-structure-template"></a>Modèle de structure d'apprentissage  
 Pour l’apprentissage de la structure d’exploration de données et ses modèles d’exploration de données associé, utilisez le [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) instruction. Le code dans l’instruction peut être divisé en parties suivantes :  
  
-   Identification de la structure d'exploration de données  
  
-   Liste des colonnes de la structure d'exploration de données  
  
-   Définition des données d'apprentissage  
  
 L'exemple générique suivant utilise l'instruction INSERT INTO :  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 La première ligne du code identifie la structure d'exploration de données à apprendre :  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 La ligne suivante du code précise les colonnes définies par la structure d'exploration de données. Vous devez répertorier chaque colonne dans la structure d'exploration de données et chaque colonne doit mapper une colonne figurant dans les données de la requête source.  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 La dernière ligne du code précise les données à utiliser pour l'apprentissage de la structure d'exploration de données :  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 Dans cette leçon, vous allez utiliser l'instruction `OPENQUERY` pour définir les données sources. Pour plus d’informations sur les autres méthodes de définition de la requête source, consultez [ &#60;requête de source de données&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Au cours de cette leçon, vous allez effectuer la tâche suivante :  
  
-   traiter la structure d'exploration de données Bike Buyer.  
  
## <a name="processing-the-predictive-mining-structure"></a>Traitement de la structure d'exploration de données prédictive  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>Pour traiter la structure d'exploration de données à l'aide de l'instruction INSERT INTO  
  
1.  Dans **Explorateur d’objets**, avec le bouton droit de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction INSERT INTO dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    [<mining structure name>]   
    ```  
  
     par :  
  
    ```  
    Bike Buyer  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <mining structure columns>  
    ```  
  
     par :  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
    [Commute Distance],  
    [Education],  
    [Gender],  
    [House Owner Flag],  
    [Marital Status],  
    [Number Cars Owned],  
    [Number Children At Home],  
    [Occupation],  
    [Region],  
    [Total Children],  
    [Yearly Income]  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     par :  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     L'instruction OPENQUERY référence la source de données [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] pour accéder à la vue vTargetMail. Cette vue contient les données sources à utiliser pour l'apprentissage des modèles d'exploration de données.  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]     
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
7.  Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Process Bike Buyer Structure.dmx`.  
  
8.  Dans la barre d’outils, cliquez sur le **Execute** bouton.  
  
 Dans la leçon suivante, vous allez explorer le contenu des modèles d'exploration de données que vous avez ajoutés à la structure d'exploration de données au cours de cette leçon.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 4 : Exploration des modèles d’exploration de données Bike Buyer](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
