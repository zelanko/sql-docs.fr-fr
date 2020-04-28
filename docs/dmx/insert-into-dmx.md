---
title: INSÉRER DANS (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 210ab8c5750fdcb38bcbca324d77eecd926042d1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68892726"
---
# <a name="insert-into-dmx"></a>INSERT INTO (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Traite l'objet d'exploration de données spécifié. Pour plus d’informations sur le traitement des modèles d’exploration de données et des structures d’exploration de données, consultez [exigences et considérations relatives au traitement &#40;&#41;d’exploration de données ](https://docs.microsoft.com/analysis-services/data-mining/processing-requirements-and-considerations-data-mining).  
  
 Si une structure d'exploration de données est spécifiée, l'instruction traite la structure et tous ses modèles d'exploration de données associés. Si un modèle d'exploration de données est spécifié, l'instruction traite uniquement le modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
INSERT INTO [MINING MODEL]|[MINING STRUCTURE] <model>|<structure> (<mapped model columns>) <source data query>  
INSERT INTO [MINING MODEL]|[MINING STRUCTURE] <model>|<structure>.COLUMN_VALUES (<mapped model columns>) <source data query>  
```  
  
## <a name="arguments"></a>Arguments  
 *model*  
 Identificateur du modèle  
  
 *structure*  
 Identificateur de la structure  
  
 *colonnes de modèle mappées*  
 Liste des identificateurs de colonnes et des identificateurs imbriqués séparés par une virgule.  
  
 *requête de données sources*  
 Requête source dans le format défini par le fournisseur  
  
## <a name="remarks"></a>Notes  
 Si vous ne spécifiez pas de **modèle** d’exploration de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] données ou de structure d’exploration de **données**, recherche le type d’objet en fonction du nom et traite l’objet correct. Si le serveur contient une structure d'exploration de données et un modèle d'exploration de données portant le même nom, une erreur est retournée.  
  
 En utilisant la deuxième forme de syntaxe, insérer dans*\<l’objet>*. COLUMN_VALUES, vous pouvez insérer des données directement dans les colonnes du modèle sans l’apprentissage du modèle. Cette méthode permet d'insérer des données de colonnes dans le modèle d'une manière concise et organisée, ce qui est utile lorsque vous utilisez des datasets contenant des hiérarchies ou des colonnes triées.  
  
 Si vous utilisez **insert into** avec un modèle d’exploration de données ou une structure d’exploration de \<données et que vous laissez les \<colonnes de modèle mappées> et les arguments de> de requête de données source, l’instruction se comporte comme **ProcessDefault**, en utilisant des liaisons qui existent déjà. Si les liaisons n'existent pas, l'instruction retourne une erreur. Pour plus d’informations sur **ProcessDefault**, consultez [options et paramètres de traitement &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services). L’exemple suivant illustre la syntaxe :  
  
```  
INSERT INTO [MINING MODEL] <model>  
```  
  
 Si vous spécifiez le **modèle d’exploration** de données et fournissez des colonnes mappées et une requête de données source, le modèle et la structure associée sont traités.  
  
 Le tableau ci-dessous donne une description du résultat de différentes formes de l'instruction, en fonction de l'état des objets.  
  
|.|État des objets|Résultats|  
|---------------|----------------------|------------|  
|Insérer dans le modèle de modèle*\<d’exploration de données>*|La structure d'exploration de données est traitée.|Le modèle d'exploration de données est traité.|  
||La structure d'exploration de données n'est pas traitée.|Le modèle et la structure d'exploration de données sont traités.|  
||La structure d'exploration de données contient des modèles d'exploration de données supplémentaires.|Échec du traitement. Vous devez retraiter la structure et les modèles d'exploration de données associés.|  
|Insérer dans la structure de structure*\<d’exploration de données>*|La structure d'exploration de données est traitée ou non.|La structure d'exploration de données et les modèles d'exploration de données associés sont traités.|  
|Insérer dans le*\<modèle* de modèle d’exploration de données>qui contient une requête source<br /><br /> or<br /><br /> Insérer dans une structure d’exploration de données*\<>* qui contient une requête source|La structure ou le modèle contient déjà du contenu.|Échec du traitement. Vous devez effacer les objets avant d’effectuer cette opération en utilisant [DELETE &#40;DMX&#41;](../dmx/delete-dmx.md).|  
  
## <a name="mapped-model-columns"></a>Mapped Model Columns  
 En utilisant les \<colonnes du modèle mappé> élément, vous pouvez mapper les colonnes de la source de données aux colonnes de votre modèle d’exploration de données. Les \<colonnes du modèle mappé> élément se présente sous la forme suivante :  
  
```  
<column identifier> | SKIP | <table identifier> (<column identifier> | SKIP), ...  
```  
  
 À l’aide de **Skip**, vous pouvez exclure certaines colonnes qui doivent exister dans la requête source, mais qui n’existent pas dans le modèle d’exploration de données. SKIP est utile lorsque vous ne contrôlez pas les colonnes incluses dans l'ensemble de lignes d'entrée. Si vous écrivez votre propre OPENQUERY, la meilleure pratique consiste à omettre la colonne de la liste de colonnes SELECT au lieu d'utiliser SKIP.  
  
 SKIP est également utile lorsqu'une colonne de l'ensemble de lignes d'entrée est nécessaire pour effectuer une jointure, mais que la colonne n'est pas utilisée par la structure d'exploration de données. En guise d'exemple typique, on peut citer une structure d'exploration de données et un modèle d'exploration de données qui contiennent une table imbriquée. L'ensemble de lignes d'entrée pour cette structure aura une colonne clé étrangère utilisée pour créer un ensemble de lignes hiérarchique à l'aide de la clause SHAPE, mais la colonne clé étrangère n'est presque jamais utilisée dans le modèle.  
  
 La syntaxe de SKIP requiert que vous insériez SKIP à la position de la colonne individuelle dans l'ensemble de lignes d'entrée qui n'a aucune colonne de structure d'exploration de données correspondante. Par exemple, dans l'exemple de table imbriquée ci-dessous, OrderNumber doit être sélectionné dans la clause APPEND afin de pouvoir être utilisé dans la clause RELATE pour spécifier la jointure ; toutefois, vous ne souhaitez pas insérer les données OrderNumber dans la table imbriquée dans la structure d'exploration de données. Par conséquent, l'exemple utilise le mot clé SKIP au lieu de OrderNumber dans l'argument INSERT INTO.  
  
## <a name="source-data-query"></a>Source Data Query  
 L' \<élément de> de requête de données source peut inclure les types de sources de données suivants :  
  
-   **OPENQUERY**  
  
-   **OPENROWSET**  
  
-   **AUTOMATIQUES**  
  
-   Toute requête [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] retournant un ensemble de lignes  
  
 Pour plus d’informations sur les types de sources de données, consultez [&#60;&#62;de requête de données source ](../dmx/source-data-query.md).  
  
## <a name="basic-example"></a>Exemple de base  
 L’exemple suivant utilise **OPENQUERY** pour effectuer l’apprentissage d’un modèle Naive Bayes basé sur les données de [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] publipostage ciblées dans la base de données.  
  
```  
INSERT INTO NBSample (CustomerKey, Gender, [Number Cars Owned],  
    [Bike Buyer])  
OPENQUERY([AdventureWorksDW2012],'Select CustomerKey, Gender, [NumberCarsOwned], [BikeBuyer]   
FROM [vTargetMail]')  
```  
  
## <a name="nested-table-example"></a>Exemple de table imbriquée  
 L’exemple suivant utilise **Shape** pour effectuer l’apprentissage d’un modèle d’exploration de données Association qui contient une table imbriquée. Notez que la première ligne contient **Skip** au lieu de OrderNumber, ce qui est requis dans l’instruction **SHAPE_APPEND** , mais n’est pas utilisé dans le modèle d’exploration de données.  
  
```  
INSERT INTO MyAssociationModel  
    ([OrderNumber],[Models] (SKIP, [Model])  
    )  
SHAPE {  
    OPENQUERY([AdventureWorksDW2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([AdventureWorksDW2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
AS [Models]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
