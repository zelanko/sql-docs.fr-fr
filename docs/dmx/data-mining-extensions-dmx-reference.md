---
title: Référence DMX (Data Mining Extensions) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c47514f551ec07a8c8837533cb38c0e6283645cd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68892881"
---
# <a name="data-mining-extensions-dmx-reference"></a>Guide de référence du langage DMX (Data Mining Extensions)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  DMX (Data Mining Extensions) est un langage que vous pouvez utiliser pour créer et utiliser des modèles d’exploration de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]données dans. Vous pouvez utiliser DMX pour créer la structure de nouveaux modèles d'exploration de données, pour l'apprentissage de ces modèles et pour les explorer, les gérer et y effectuer des prévisions. Le langage DMX se compose d'instructions DDL (langage de définition de données), d'instructions DML (langage de manipulation de données), de fonctions et d'opérateurs.  
  
## <a name="microsoft-ole-db-for-data-mining-specification"></a>Spécification Microsoft OLE DB pour l'exploration de données  
 Les fonctionnalités d’exploration de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] données de sont conçues pour se conformer aux OLE DB pour la [!INCLUDE[msCoName](../includes/msconame-md.md)] spécification d’exploration de données.  
  
 La [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB pour la spécification d’exploration de données définit les éléments suivants :  
  
-   Une structure pour conserver les informations qui définissent un modèle d'exploration de données.  
  
-   Un langage pour créer et utiliser des modèles d'exploration de données.  
  
 La spécification définit la base de l'exploration de données comme étant l'objet virtuel de modèle d'exploration de données. L'objet de modèle d'exploration de données encapsule tout ce qui est connu concernant un modèle d'exploration de données particulier. L'objet de modèle d'exploration de données est structuré comme une table SQL, avec des colonnes, des types de données et des méta-informations qui décrivent le modèle. Cette structure vous permet d'employer le langage DMX, qui est une extension du langage SQL, pour créer des modèles et les utiliser.  
  
 **Pour plus d’informations, procédez comme suit :** [structures d’exploration de données &#40;Analysis Services d’exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-structures-analysis-services-data-mining)  
  
##  <a name="dmx-statements"></a><a name="BKMK_DMXStatements"></a>Instructions DMX  
 Vous pouvez utiliser des instructions DMX pour créer, traiter, supprimer, copier, explorer et effectuer des prévisions dans des modèles d'exploration de données. Il existe deux types d'instructions DMX : les instructions de définition de données et les instructions de manipulation de données. Chaque type d'instruction permet d'effectuer différentes sortes de tâches.  
  
 Les sections suivantes fournissent des informations supplémentaires sur l'utilisation des instructions DMX :  
  
-   [Instructions de définition de données](#BKMK_DDL)  
  
-   [Instructions de manipulation de données](#BKMK_DML)  
  
-   [Notions de base des requêtes](#BKMK_Queries)  
  
###  <a name="data-definition-statements"></a><a name="BKMK_DDL"></a>Instructions de définition de données  
 Les instructions de définition de données dans DMX permettent de créer et de définir de nouvelles structures et modèles d'exploration de données, d'importer et d'exporter des modèles et des structures d'exploration de données et de supprimer des modèles existants d'une base de données. Les instructions de définition de données dans DMX font partie du langage de définition de données (DDL).  
  
 En utilisant les instructions de définition de données dans DMX, vous pouvez effectuer les tâches suivantes :  
  
-   Créez une structure d’exploration de données à l’aide de l’instruction [Create Mining structure](../dmx/create-mining-structure-dmx.md) et ajoutez un modèle d’exploration de données à la structure d’exploration de données à l’aide de l’instruction [ALTER Mining structure](../dmx/alter-mining-structure-dmx.md) .  
  
-   Créez simultanément un modèle d’exploration de données et une structure d’exploration de données associée à l’aide de l’instruction [Create Mining Model](../dmx/create-mining-model-dmx.md) pour créer un objet de modèle d’exploration de données vide.  
  
-   Exportez un modèle d’exploration de données et la structure d’exploration de données associée dans un fichier à l’aide de l’instruction [Export](../dmx/export-dmx.md) . Importez un modèle d’exploration de données et une structure d’exploration de données associée à partir d’un fichier créé par l’instruction EXPORT à l’aide de l’instruction [Import](../dmx/import-dmx.md) .  
  
-   Copiez la structure d’un modèle d’exploration de données existant dans un nouveau modèle, puis exercez-la avec les mêmes données, à l’aide de l’instruction [SELECT INTO](../dmx/select-into-dmx.md) .  
  
-   Supprimer complètement un modèle d’exploration de données d’une base de données à l’aide de l’instruction [Drop Mining Model](../dmx/drop-mining-model-dmx.md) . Supprimez complètement une structure d’exploration de données et tous ses modèles d’exploration de données associés de la base de données à l’aide de l’instruction [Drop Mining structure](../dmx/drop-mining-structure-dmx.md) .  
  
 Pour en savoir plus sur les tâches d’exploration de données que vous pouvez effectuer à l’aide d’instructions DMX, consultez [Data Mining Extensions &#40;dmx&#41; instruction Reference](../dmx/data-mining-extensions-dmx-statements.md).  
  
 [Retour à Instructions DMX](#BKMK_DMXStatements)  
  
###  <a name="data-manipulation-statements"></a><a name="BKMK_DML"></a>Instructions de manipulation de données  
 Les instructions de manipulation de données dans DMX permettent d'utiliser des modèles d'exploration de données existants, d'explorer ces modèles et de créer des prévisions dans ces derniers. Les instructions de manipulation de données dans DMX font partie du langage de manipulation de données (DML).  
  
 En utilisant les instructions de manipulation de données dans DMX, vous pouvez effectuer les tâches suivantes :  
  
-   Effectuer l’apprentissage d’un modèle d’exploration de données à l’aide de l’instruction [insert into](../dmx/insert-into-dmx.md) . Cette opération n'insert pas les données source réelles dans un modèle d'exploration de données, mais crée plutôt une abstraction qui décrit le modèle d'exploration de données que l'algorithme crée. La requête source d’une instruction INSERT INTO est décrite dans [ \<>des requêtes de données sources ](../dmx/source-data-query.md).  
  
-   Étendez l’instruction SELECT pour parcourir les informations calculées lors de l’apprentissage du modèle et stockées dans le modèle d’exploration de données, telles que les statistiques des données sources. Voici les clauses que vous pouvez inclure pour étendre la puissance de l’instruction SELECT :  
  
    -   [SELECT DISTINCT FROM &#60;modèle &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
    -   [Sélectionnez &#60;&#62; de modèle. &#40;DE CONTENU DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
    -   [Sélectionnez &#60;&#62; de modèle. CAS &#40;&#41;DMX](../dmx/select-from-model-cases-dmx.md)  
  
    -   [Sélectionnez &#60;&#62; de modèle.&#41;SAMPLE_CASES &#40;DMX](../dmx/select-from-model-sample-cases-dmx.md)  
  
    -   [Sélectionnez &#60;&#62; de modèle.&#41;DIMENSION_CONTENT &#40;DMX](../dmx/select-from-model-dimension-content-dmx.md)  
  
-   Créez des prédictions basées sur un modèle d’exploration de données existant à l’aide de la clause [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) de l’instruction SELECT. La requête source pour une instruction PREDICTION JOIN est décrite dans [ \<>de requête de données sources ](../dmx/source-data-query.md).  
  
-   Supprimer toutes les données formées d’un modèle ou d’une structure à l’aide de l’instruction [DELETE &#40;DMX&#41;](../dmx/delete-dmx.md) .  
  
 Pour en savoir plus sur les tâches d’exploration de données que vous pouvez effectuer à l’aide d’instructions DMX, consultez [Data Mining Extensions &#40;dmx&#41; instruction Reference](../dmx/data-mining-extensions-dmx-statements.md).  
  
 [Retour à Instructions DMX](#BKMK_DMXStatements)  
  
###  <a name="dmx-query-fundamentals"></a><a name="BKMK_Queries"></a>Notions de base des requêtes DMX  
 L’instruction SELECT est la base de la plupart des requêtes DMX. En fonction des clauses que vous utilisez avec ce type d'instruction, vous pouvez explorer ou copier des modèles d'exploration de données, ou effectuer des prévisions dans ces derniers. La requête de prédiction utilise une forme sélectionner pour créer des prédictions basées sur des modèles d’exploration de données existants. Des fonctions augmentent vos capacités à explorer et interroger les modèles d'exploration de données au-delà des possibilités intrinsèques du modèle d'exploration de données.   
  
 Les fonctions DMX permettent d'obtenir des informations qui sont découvertes au cours de l'apprentissage de vos modèles, et de calculer de nouvelles informations. Ces fonctions peuvent être utilisées pour différents objectifs, notamment pour retourner des statistiques décrivant les données sous-jacentes ou l'exactitude d'une prévision ou pour retourner l'explication développée d'une prévision.  
  
 **Pour plus d'****informations :** [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md), [fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md), [structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md), informations de référence sur les fonctions [DMX (Data Mining Extensions &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md) )    
  
 [Retour à Instructions DMX](#BKMK_DMXStatements)  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
