---
title: 'Leçon 1 : création de la structure d’exploration de données vélo Buyer | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6384910858d87a80aa3c8f897bc88e45f4504fb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62678501"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a>Leçon 1 : Création de la structure d’exploration de données Bike Buyer
  Dans cette leçon, vous allez créer une structure d'exploration de données à l'aide de laquelle vous pouvez prévoir si un acheteur potentiel de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] est intéressé par l'achat d'un vélo. Si vous n’êtes pas familiarisé avec les structures d’exploration de données et leur rôle dans l’exploration de données, consultez structures d’exploration de données [&#40;Analysis Services-exploration de données&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 La structure d’exploration de données Bike Buyer que vous allez créer dans cette leçon prend en charge l’ajout de modèles d’exploration de données basés sur l’algorithme [Microsoft Clustering](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)d’algorithmes[Microsoft Decision Trees](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md). Au cours d'autres leçons, vous utiliserez les modèles d'exploration de données clustering pour examiner différentes méthodes de regroupement des clients et exploiterez les modèles d'exploration de données d'arbre de décision pour déterminer si un client potentiel est susceptible d'acheter un vélo.  
  
## <a name="create-mining-structure-statement"></a>Instruction CREATE MINING STRUCTURE  
 Pour créer une structure d’exploration de données, vous utilisez l’instruction [Create Mining structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) . Le code de l’instruction peut être divisé en plusieurs parties :  
  
-   Attribution d'un nom à la structure.  
  
-   Définition de la colonne clé.  
  
-   Définition des colonnes d'exploration de données.  
  
-   Définition d'un jeu de données de test facultatif.  
  
 L'exemple générique suivant utilise l'instruction CREATE MINING STRUCTURE :  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
(  
    <key column>,  
    <mining structure columns>  
)   
WITH HOLDOUT (<holdout specifier>)  
```  
  
 La première ligne du code définit le nom de la structure :  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
```  
  
 Pour plus d’informations sur l’attribution d’un nom à un objet dans les extensions DMX (Data Mining Extensions), consultez [identificateurs &#40;dmx&#41;](/sql/dmx/identifiers-dmx).  
  
 La ligne suivante du code définit la colonne clé de la structure d'exploration de données qui identifie de manière unique une entité au sein des données source :  
  
```  
<key column>,  
```  
  
 Dans la structure d'exploration de données que vous allez créer, l'identificateur du client, `CustomerKey`, définit une entité dans les données sources.  
  
 La ligne suivante du code permet de définir les colonnes d'exploration de données qu'utilisent les modèles d'exploration de données associés à la structure d'exploration de données :  
  
```  
<mining structure columns>  
```  
  
 Vous pouvez utiliser la fonction discrétisation dans \<les colonnes de structure d’exploration de données> pour discrétisationr des colonnes continues à l’aide de la syntaxe suivante :  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 Pour plus d’informations sur la discrétisation des colonnes, consultez [méthodes de discrétisation &#40;&#41;d’exploration de données ](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md). Pour plus d’informations sur les types de colonnes de structure d’exploration de données que vous pouvez définir, consultez [colonnes de structure d’exploration](../../2014/analysis-services/data-mining/mining-structure-columns.md)de données.  
  
 La dernière ligne du code définit une partition facultative dans la structure d'exploration de données :  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 Vous spécifiez une partie des données à utiliser pour tester des modèles d'exploration de données associés à la structure, puis les données restantes sont utilisées pour l'apprentissage des modèles. Par défaut, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] crée un jeu de données de test qui contient 30 pour cent de toutes les données de cas. Vous ajoutez ensuite la spécification selon laquelle le jeu de données de test doit contenir 30 pour cent des cas jusqu'à un maximum de 1000 cas. Si 30 pour cent des cas représente moins de 1000, le jeu de données de test contient alors la plus petite quantité.  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
-   créer une nouvelle requête vide ;  
  
-   Modifiez la requête pour créer la structure d’exploration de données.  
  
-   exécutez la requête.  
  
## <a name="creating-the-query"></a>Création de la requête  
 La première étape consiste à se connecter à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et à créer une nouvelle requête DMX dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>Pour créer une requête DMX dans SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Dans la boîte de dialogue **se connecter au serveur** , pour **type de serveur**, sélectionnez **Analysis Services**. Dans **nom du serveur**, `LocalHost`tapez ou tapez le nom de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à laquelle vous souhaitez vous connecter pour cette leçon. Cliquez sur **Connecter**.  
  
3.  Dans **l’Explorateur d’objets**, cliquez avec le bouton [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]droit sur l’instance de, pointez sur **nouvelle requête**, puis cliquez sur **DMX** pour ouvrir l' **éditeur de requête** et une nouvelle requête vide.  
  
## <a name="altering-the-query"></a>Modification de la requête  
 L'étape suivante implique de modifier l'instruction CREATE MINING STRUCTURE décrite ci-avant en vue de créer la structure d'exploration de données Bike Buyer.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>Pour personnaliser l'instruction CREATE MINING STRUCTURE  
  
1.  Dans l'Éditeur de requête, copiez l'exemple générique de l'instruction CREATE MINING STRUCTURE dans la requête vide.  
  
2.  Remplacez le code suivant :  
  
    ```  
    [<mining structure>]   
    ```  
  
     par :  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  Remplacez le code suivant :  
  
    ```  
    <key column>   
    ```  
  
     par :  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <mining structure columns>   
    ```  
  
     par :  
  
    ```  
    [Age] LONG DISCRETIZED(Automatic,10),  
    [Bike Buyer] LONG DISCRETE,  
    [Commute Distance] TEXT DISCRETE,  
    [Education] TEXT DISCRETE,  
    [Gender] TEXT DISCRETE,  
    [House Owner Flag] TEXT DISCRETE,  
    [Marital Status] TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Number Children At Home] LONG DISCRETE,  
    [Occupation] TEXT DISCRETE,  
    [Region] TEXT DISCRETE,  
    [Total Children]LONG DISCRETE,  
    [Yearly Income] DOUBLE CONTINUOUS  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    WITH HOLDOUT (holdout specifier>)  
    ```  
  
     par :  
  
    ```  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
    ```  
  
     L'instruction complète de la structure d'exploration de données doit se présenter comme suit :  
  
    ```  
    CREATE MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key] LONG KEY,  
       [Age]LONG DISCRETIZED(Automatic,10),  
       [Bike Buyer] LONG DISCRETE,  
       [Commute Distance] TEXT DISCRETE,  
       [Education] TEXT DISCRETE,  
       [Gender] TEXT DISCRETE,  
       [House Owner Flag] TEXT DISCRETE,  
       [Marital Status] TEXT DISCRETE,  
       [Number Cars Owned]LONG DISCRETE,  
       [Number Children At Home]LONG DISCRETE,  
       [Occupation] TEXT DISCRETE,  
       [Region] TEXT DISCRETE,  
       [Total Children]LONG DISCRETE,  
       [Yearly Income] DOUBLE CONTINUOUS  
    )  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
  
    ```  
  
6.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
7.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `Bike Buyer Structure.dmx`.  
  
## <a name="executing-the-query"></a>Exécution de la requête  
 La dernière étape concerne l'exécution de la requête. Après avoir créé et enregistrée une requête, elle doit être exécutée. Autrement dit, l'instruction doit être exécutée pour créer la structure d'exploration de données sur le serveur. Pour plus d’informations sur l’exécution de requêtes dans l’éditeur de requête, consultez [moteur de base de données l’éditeur de requête &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>Pour exécuter la requête  
  
1.  Dans l’éditeur de requête, dans la barre d’outils, cliquez sur **exécuter**.  
  
     L’état de la requête s’affiche dans l’onglet **messages** en bas de l’éditeur de requête à la fin de l’exécution de l’instruction. Les messages doivent révéler le texte suivant :  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Une nouvelle structure nommée **vélo Buyer** existe désormais sur le serveur.  
  
 Dans la leçon suivante, vous allez ajouter des modèles d'exploration de données à la structure que vous venez de créer.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Ajout de modèles d’exploration de données à la structure d’exploration de données Bike Buyer](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
