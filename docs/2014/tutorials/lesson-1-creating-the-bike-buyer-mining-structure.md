---
title: 'Leçon 1 : Création de la Structure d’exploration de données Bike Buyer | Microsoft Docs'
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62678501"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a>Leçon 1 : Création de la structure d’exploration de données Bike Buyer
  Dans cette leçon, vous allez créer une structure d'exploration de données à l'aide de laquelle vous pouvez prévoir si un acheteur potentiel de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] est intéressé par l'achat d'un vélo. Si vous n’êtes pas familiarisé avec les structures d’exploration de données et leur rôle dans l’exploration de données, consultez [les Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 La structure d’exploration de données Bike Buyer que vous allez créer dans cette leçon prend en charge l’ajout de modèles d’exploration de données selon le [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[algorithme d’arbres de décision de Microsoft](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md). Au cours d'autres leçons, vous utiliserez les modèles d'exploration de données clustering pour examiner différentes méthodes de regroupement des clients et exploiterez les modèles d'exploration de données d'arbre de décision pour déterminer si un client potentiel est susceptible d'acheter un vélo.  
  
## <a name="create-mining-structure-statement"></a>Instruction CREATE MINING STRUCTURE  
 Pour créer une structure d’exploration de données, vous utilisez le [CREATE MINING STRUCTURE &#40;DMX&#41; ](/sql/dmx/create-mining-structure-dmx) instruction. Le code dans l’instruction peut être divisé en parties suivantes :  
  
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
  
 Pour plus d’informations sur l’appellation d’un objet dans les Extensions DMX (Data Mining), consultez [identificateurs &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 La ligne suivante du code définit la colonne clé de la structure d'exploration de données qui identifie de manière unique une entité au sein des données source :  
  
```  
<key column>,  
```  
  
 Dans la structure d'exploration de données que vous allez créer, l'identificateur du client, `CustomerKey`, définit une entité dans les données sources.  
  
 La ligne suivante du code permet de définir les colonnes d'exploration de données qu'utilisent les modèles d'exploration de données associés à la structure d'exploration de données :  
  
```  
<mining structure columns>  
```  
  
 Vous pouvez utiliser la fonction DISCRETIZE dans \<colonnes de structure d’exploration de données > pour discrétiser les colonnes continues à l’aide de la syntaxe suivante :  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 Pour plus d’informations sur la discrétisation des colonnes, consultez [méthodes de discrétisation &#40;d’exploration de données&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md). Pour plus d’informations sur les types de colonnes que vous pouvez définir de la structure d’exploration de données, consultez [les colonnes de Structure d’exploration de données](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
 La dernière ligne du code définit une partition facultative dans la structure d'exploration de données :  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 Vous spécifiez une partie des données à utiliser pour tester des modèles d'exploration de données associés à la structure, puis les données restantes sont utilisées pour l'apprentissage des modèles. Par défaut, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] crée un jeu de données de test qui contient 30 pour cent de toutes les données de cas. Vous ajoutez ensuite la spécification selon laquelle le jeu de données de test doit contenir 30 pour cent des cas jusqu'à un maximum de 1000 cas. Si 30 pour cent des cas représente moins de 1000, le jeu de données de test contient alors la plus petite quantité.  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Vous allez effectuer les tâches suivantes dans cette leçon :  
  
-   créer une nouvelle requête vide ;  
  
-   Modifier la requête pour créer la structure d’exploration de données.  
  
-   exécutez la requête.  
  
## <a name="creating-the-query"></a>Création de la requête  
 La première étape consiste à se connecter à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et à créer une nouvelle requête DMX dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>Pour créer une requête DMX dans SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Dans le **se connecter au serveur** boîte de dialogue pour **type de serveur**, sélectionnez **Analysis Services**. Dans **nom du serveur**, type `LocalHost`, ou tapez le nom de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que vous souhaitez vous connecter à pour cette leçon. Cliquer sur **Se connecter**.  
  
3.  Dans **Explorateur d’objets**, avec le bouton droit de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pointez sur **nouvelle requête**, puis cliquez sur **DMX** pour ouvrir le **éditeur de requête**et une nouvelle requête vide.  
  
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
  
6.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
7.  Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Bike Buyer Structure.dmx`.  
  
## <a name="executing-the-query"></a>L’exécution de la requête  
 La dernière étape concerne l'exécution de la requête. Après avoir créé et enregistrée une requête, elle doit être exécutée. Autrement dit, l'instruction doit être exécutée pour créer la structure d'exploration de données sur le serveur. Pour plus d’informations sur l’exécution de requêtes dans l’éditeur de requête, consultez [éditeur de requête du moteur de base de données &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>Pour exécuter la requête  
  
1.  Dans l’éditeur de requête, dans la barre d’outils, cliquez sur **Execute**.  
  
     L’état de la requête est affiché dans le **Messages** onglet en bas de l’éditeur de requête une fois l’instruction terminée l’exécution. Les messages doivent révéler le texte suivant :  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Une nouvelle structure appelée **Bike Buyer** existe maintenant sur le serveur.  
  
 Dans la leçon suivante, vous allez ajouter des modèles d'exploration de données à la structure que vous venez de créer.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Ajout des modèles d’exploration de données à la Structure d’exploration de données Bike Buyer](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
