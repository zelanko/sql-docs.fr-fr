---
title: 'Leçon 1 : Création de la Structure d’exploration de données Market Basket | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f719a4dd11234a361856dcf170eebcd3856f66c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323609"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a>Leçon 1 : Création de la structure d'exploration de données Market Basket
  Dans cette leçon, vous allez créer une structure d'exploration de données à l'aide de laquelle vous pouvez prévoir quels produits [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] un client est susceptible d'acheter simultanément. Si vous n’êtes pas familiarisé avec les structures d’exploration de données et leur rôle dans l’exploration de données, consultez [les Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 La structure d’exploration de données association que vous allez créer dans cette leçon prend en charge l’ajout de modèles d’exploration de données selon le [algorithme Microsoft Association](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md). Au cours d'autres leçons, vous utiliserez les modèles d'exploration de données pour prévoir les types de produits qu'un client est susceptible d'acheter en même temps (on parle dans ce cas d'analyse de panier d'achat). Par exemple, vous découvrirez peut-être que des clients peuvent acheter en même temps des VTT, des pneus et des casques.  
  
 Dans cette leçon, la structure d'exploration de données est définie à l'aide de tables imbriquées. Les tables imbriquées sont utilisées puisque le domaine de données défini par la structure apparaît dans deux tables source différentes. Pour plus d’informations sur les tables imbriquées, consultez [des Tables imbriquées &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
## <a name="create-mining-structure-statement"></a>Instruction CREATE MINING STRUCTURE  
 Pour créer une structure d’exploration de données contenant une table imbriquée, vous utilisez le [CREATE MINING STRUCTURE &#40;DMX&#41; ](/sql/dmx/create-mining-structure-dmx) instruction. Le code dans l’instruction peut être divisé en parties suivantes :  
  
-   Attribution d'un nom à la structure  
  
-   Définition de la colonne clé  
  
-   Définition des colonnes d'exploration de données  
  
-   Définition des colonnes de la table imbriquée  
  
 L'exemple générique suivant utilise l'instruction CREATE MINING STRUCTURE :  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 La première ligne du code définit le nom de la structure :  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 Pour plus d’informations sur l’appellation d’un objet dans DMX, consultez [identificateurs &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 La ligne suivante du code définit la colonne clé de la structure d'exploration de données qui identifie de manière unique une entité au sein des données source :  
  
```  
<key column>  
```  
  
 La ligne suivante du code permet de définir les colonnes d'exploration de données qu'utilisent les modèles d'exploration de données associés à la structure d'exploration de données :  
  
```  
<mining structure columns>  
```  
  
 Les lignes suivantes du code définissent les colonnes de la table imbriquée :  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 Pour plus d’informations sur les types de colonnes que vous pouvez définir de la structure d’exploration de données, consultez [les colonnes de Structure d’exploration de données](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
> [!NOTE]  
>  Par défaut, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] crée un jeu de données d'exclusion de 30 pour cent pour chaque structure d'exploration de données ; toutefois, lorsque vous utilisez DMX pour créer une structure d'exploration de données, vous devez ajouter manuellement le jeu de données d'exclusion, le cas échéant.  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Vous allez effectuer les tâches suivantes dans cette leçon :  
  
-   créer une requête vide ;  
  
-   modifier la requête pour créer la structure d'exploration de données ;  
  
-   exécuter la requête.  
  
## <a name="creating-the-query"></a>Création de la requête  
 La première étape consiste à se connecter à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et à créer une nouvelle requête DMX dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>Pour créer une requête DMX dans SQL Server Management Studio  
  
1.  Ouvrir [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Dans le **se connecter au serveur** boîte de dialogue pour **type de serveur**, sélectionnez **Analysis Services**. Dans **nom du serveur**, type `LocalHost`, ou le nom de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que vous souhaitez vous connecter à pour cette leçon. Cliquez sur **Se connecter**.  
  
3.  Dans **Explorateur d’objets**, avec le bouton droit de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
## <a name="altering-the-query"></a>Modification de la requête  
 L'étape suivante implique de modifier l'instruction CREATE MINING STRUCTURE décrite ci-avant en vue de créer la structure d'exploration de données Market Basket.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>Pour personnaliser l'instruction CREATE MINING STRUCTURE  
  
1.  Dans l’éditeur de requête, copiez l’exemple générique de l’instruction CREATE MINING STRUCTURE dans la requête vide.  
  
2.  Remplacez le code suivant :  
  
    ```  
    [mining structure name]   
    ```  
  
     par :  
  
    ```  
    [Market Basket]  
    ```  
  
3.  Remplacez le code suivant :  
  
    ```  
    <key column>  
    ```  
  
     par :  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     par :  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     Le langage TEXT KEY précise que la colonne Model est la colonne clé de la table imbriquée.  
  
     L'instruction complète de la structure d'exploration de données doit se présenter comme suit :  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
6.  Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Market Basket Structure.dmx`.  
  
## <a name="executing-the-query"></a>L’exécution de la requête  
 La dernière étape concerne l'exécution de la requête. Après avoir été créée et enregistrée, la requête doit être exécutée (l'instruction doit être exécutée) pour permettre la création de la structure d'exploration de données sur le serveur. Pour plus d’informations sur l’exécution de requêtes dans l’éditeur de requête, consultez [éditeur de requête du moteur de base de données &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>Pour exécuter la requête  
  
-   Dans l’éditeur de requête, dans la barre d’outils, cliquez sur **Execute**.  
  
     L’état de la requête est affiché dans le **Messages** onglet en bas de l’éditeur de requête une fois l’instruction terminée l’exécution. Les messages doivent révéler le texte suivant :  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Une nouvelle structure appelée **Market Basket** existe maintenant sur le serveur.  
  
 Dans la leçon suivante, vous allez ajouter des modèles d'exploration de données à la structure Market Basket que vous venez de créer.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Ajout de modèles d’exploration de données à la structure d’exploration de données Market Basket](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
