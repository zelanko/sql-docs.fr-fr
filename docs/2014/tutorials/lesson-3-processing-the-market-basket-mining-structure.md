---
title: 'Leçon 3 : Traitement de la Structure d’exploration de données de panier d’achat | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095a043f-cf6f-45bb-a021-ae4e1b535c65
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce2c2e6944d524a38edc331d2cd128ca7cf7d419
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018261"
---
# <a name="lesson-3-processing-the-market-basket-mining-structure"></a>Leçon 3 : Traitement de la structure d'exploration de données Market Basket
  Dans cette leçon, vous allez utiliser le [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) instruction et vAssocSeqLineItems et vAssocSeqOrders à partir de la [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] base de données exemple pour traiter les structures d’exploration et l’exploration des modèles que vous avez créé dans [leçon 1 : Création de la Structure d’exploration de données de panier](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md) et [leçon 2 : Ajout des modèles d’exploration de données à la Structure d’exploration de données Market Basket](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).  
  
 Lorsque vous traitez une structure d'exploration de données, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] lit les données sources et génère les structures qui soutiennent les modèles d'exploration de données. Lorsque vous traitez un modèle d’exploration de données, les données définies par la structure d’exploration de données sont transmises via l’algorithme d’exploration de données que vous avez choisi. L'algorithme recherche des tendances et des modèles, puis stocke les informations recueillies dans le modèle d'exploration de données. Par conséquent, le modèle d'exploration de données ne contient pas les données source réelles mais plutôt les informations recueillies par l'algorithme. Pour plus d’informations sur les modèles d’exploration de données de traitement, consultez [traitement des exigences et considérations &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Si vous modifiez une colonne de structure ou les données source, vous devez simplement retraiter la structure d'exploration de données. Si vous ajoutez un modèle d'exploration de données à une structure d'exploration de données déjà traitée, vous pouvez utiliser l'instruction `INSERT INTO MINING MODEL` pour effectuer l'apprentissage du nouveau modèle d'exploration de données sur les données existantes.  
  
 Comme la structure d'exploration de données Market Basket contient une table imbriquée, vous devez définir les colonnes d'exploration de données sur lesquelles effectuer l'apprentissage à l'aide de la structure de la table imbriquée et utiliser la commande `SHAPE` pour définir les requêtes chargées d'extraire les données d'apprentissage à partir des tables source.  
  
## <a name="insert-into-statement"></a>Instruction INSERT INTO  
 Pour l’apprentissage de la structure d’exploration de données Market Basket et ses modèles d’exploration de données associé, utilisez le [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) instruction. Le code de cette instruction peut être divisé selon les sections suivantes :  
  
-   Identification de la structure d'exploration de données  
  
-   Liste des colonnes de la structure d'exploration de données  
  
-   Définition des données d'apprentissage à l'aide de l'instruction `SHAPE`  
  
 L'exemple générique suivant utilise l'instruction `INSERT INTO` :  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],'<nested SELECT statement>')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 La première ligne du code identifie la structure d'exploration de données à apprendre :  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Les lignes suivantes du code précisent les colonnes définies par la structure d'exploration de données. Vous devez répertorier chaque colonne dans la structure d'exploration de données et chaque colonne doit mapper une colonne figurant dans les données de la requête source. Vous pouvez utiliser la commande `SKIP` pour ignorer les colonnes qui existent dans les données source, mais non dans la structure d'exploration de données. Pour plus d’informations sur l’utilisation `SKIP`, consultez [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx).  
  
```  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
```  
  
 Les dernières lignes du code précisent les données à utiliser pour l'apprentissage de la structure d'exploration de données. Comme les données source figurent dans deux tables, vous allez faire appel à l'instruction `SHAPE` pour relier les tables.  
  
```  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],''<nested SELECT statement>'')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 Dans cette leçon, vous allez utiliser l'instruction `OPENQUERY` pour définir les données sources. Pour plus d’informations sur les autres méthodes de définition d’une requête sur la source de données, consultez [ &#60;requête de source de données&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Au cours de cette leçon, vous allez effectuer la tâche suivante :  
  
-   traiter la structure d'exploration de données Market Basket.  
  
## <a name="processing-the-market-basket-mining-structure"></a>Traitement de la structure d'exploration de données Market Basket  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>Pour traiter la structure d'exploration de données à l'aide de l'instruction INSERT INTO  
  
1.  Dans **Explorateur d’objets**, avec le bouton droit de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction INSERT INTO dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    [<mining structure>]  
    ```  
  
     par :  
  
    ```  
    Market Basket  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    <mining structure columns>  
    [<nested table>]  
    ( SKIP, <skipped column> )  
    ```  
  
     par :  
  
    ```  
    [OrderNumber],  
    [Products]   
    (SKIP, [Model])  
    ```  
  
     Dans l'instruction, `Products` fait référence à la table Products définie par l'instruction SHAPE. `SKIP` est utilisé pour ignorer la colonne du modèle, qui existe dans les données sources comme clé, mais n'est pas utilisée par la structure d'exploration de données.  
  
5.  Remplacez le code suivant :  
  
    ```  
    SHAPE {  
      OPENQUERY([<datasource>],'<SELECT statement>') }  
    APPEND  
    (   
      {OPENQUERY([<datasource>],'<nested SELECT statement>')  
    }  
    RELATE [<case key>] TO [<foreign key>]  
    ) AS [<nested table>]  
    ```  
  
     par :  
  
    ```  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
     La requête source fait référence le [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] source de données définie dans le [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] exemple de projet. Elle utilise la source de données pour accéder aux vues vAssocSeqLineItems et vAssocSeqOrders. Ces vues renferment les données source à utiliser pour effectuer l'apprentissage du modèle d'exploration de données. Si vous n’avez pas créé ce projet ou ces vues, consultez [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
     Dans la commande `SHAPE`, vous allez utiliser `OPENQUERY` pour définir deux requêtes. La première requête définit la table parente, la deuxième définit la table imbriquée. Les deux tables sont associées par le biais de la colonne OrderNumber présente dans les deux tables.  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    INSERT INTO MINING STRUCTURE [Market Basket]  
    (  
       [OrderNumber],[Products] (SKIP, [Model])  
    )  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
6.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
7.  Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Process Market Basket.dmx`.  
  
8.  Dans la barre d’outils, cliquez sur le **Execute** bouton.  
  
 Après avoir terminé d'exécuter la requête, vous pouvez consulter les modèles et les jeux d'éléments trouvés, consulter les associations ou filtrer par jeu d'éléments, probabilité ou importance. Pour afficher ces informations, dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], cliquez sur le nom du modèle de données, puis cliquez sur **Parcourir**.  
  
 Dans la leçon suivante, vous allez créer plusieurs prédictions fondées sur les modèles d'exploration de données que vous avez ajoutés à la structure Market Basket.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 4 : L’exécution de prédictions Market Basket](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
  
  
