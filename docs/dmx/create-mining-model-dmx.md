---
title: CRÉER UN MODÈLE D’EXPLORATION DE DONNÉES (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e7215f50705b593130a69cfe076f0878b0ac03d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68889076"
---
# <a name="create-mining-model-dmx"></a>CREATE MINING MODEL (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Crée à la fois un modèle d'exploration de données et une structure d'exploration de données dans la base de données. Vous pouvez créer un modèle en définissant le nouveau modèle dans l'instruction ou en utilisant le langage PMML (Predictive Model Markup Language). La deuxième option s'adresse uniquement aux utilisateurs expérimentés.  
  
 La structure d'exploration de données est nommée en annexant "_structure" au nom du modèle, ce qui garantit l'unicité du nom de la structure dans le nom du modèle.  
  
 Pour créer un modèle d’exploration de données pour une structure d’exploration de données existante, utilisez l’instruction [ALTER Mining structure &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE [SESSION] MINING MODEL <model>  
(  
    [(<column definition list>)]  
)  
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH]  
CREATE MINING MODEL <model> FROM PMML <xml string>  
```  
  
## <a name="arguments"></a>Arguments  
 *model*  
 Nom unique du modèle  
  
 *liste de définitions de colonnes*  
 Liste des définitions de colonnes séparées par des virgules.  
  
 *utilisé*  
 Nom d'un algorithme d'exploration de données, tel que défini par le fournisseur actuel.  
  
> [!NOTE]  
>  Une liste des algorithmes pris en charge par le fournisseur actuel peut être récupérée à l’aide de [DMSCHEMA_MINING_SERVICES ensemble de lignes](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset). Pour afficher les algorithmes pris en charge dans l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]actuelle de, consultez [propriétés d’exploration de données](https://docs.microsoft.com/analysis-services/server-properties/data-mining-properties).  
  
 *liste de paramètres*  
 facultatif. Liste séparée par des virgules des paramètres définis par le fournisseur de l'algorithme.  
  
 *Chaîne XML*  
 (Pour une utilisation avancée uniquement.) Un modèle encodé XML (PMML). La chaîne doit être entourée de guillemets simples (').  
  
 La clause **session** vous permet de créer un modèle d’exploration de données qui est automatiquement supprimé du serveur lors de la fermeture de la connexion ou de l’expiration de la session. Les modèles d’exploration de données de **session** sont utiles car ils n’exigent pas que l’utilisateur soit administrateur de base de données, et ils n’utilisent l’espace disque que tant que la connexion est ouverte.  
  
 La clause **with Drillthrough** permet d’extraire le nouveau modèle d’exploration de données. L'extraction ne peut être activée que lors de la création du modèle. Pour certains types de modèles, l'extraction est requise pour parcourir le modèle dans la visionneuse personnalisée. L'extraction n'est pas requise pour la prédiction ou pour parcourir le modèle à l'aide de la Visionneuse de l'arborescence de contenu générique Microsoft.  
  
 L’instruction **Create Mining Model** crée un nouveau modèle d’exploration de données basé sur la liste de définitions de colonnes, l’algorithme et la liste de paramètres d’algorithme.  
  
### <a name="column-definition-list"></a>Liste des définitions de colonnes  
 Pour définir la structure d'un modèle qui utilise la liste des définitions de colonnes, vous devez fournir les informations suivantes pour chaque colonne :  
  
-   Nom (obligatoire)  
  
-   Type de données (obligatoire)  
  
-   Distribution  
  
-   Liste des indicateurs de modélisation  
  
-   Type de contenu (obligatoire)  
  
-   Demande de prédiction, qui indique à l’algorithme de prédire cette colonne, indiquée par la clause **Predict** ou **PREDICT_ONLY**  
  
-   Relation à une colonne d’attributs (obligatoire uniquement si elle s’applique), indiquée par la clause **related to**  
  
 Utilisez la syntaxe suivante pour la liste des définitions de colonnes, pour définir une seule colonne :  
  
```  
<column name>    <data type>    [<Distribution>]    [<Modeling Flags>]    <Content Type>    [<prediction>]    [<column relationship>]   
```  
  
 Utilisez la syntaxe suivante pour la liste des définitions de colonnes, pour définir une colonne de tables imbriquées :  
  
```  
<column name>    TABLE    [<prediction>] ( <non-table column definition list> )  
```  
  
 À l'exception des indicateurs de modélisation, vous ne pouvez utiliser qu'une seule clause d'un groupe particulier pour définir une colonne. Vous pouvez définir plusieurs indicateurs de modélisation pour une colonne.  
  
 Pour la liste des types de données, types de contenu, distributions de colonnes et indicateurs de modélisation à utiliser pour définir une colonne, consultez les rubriques suivantes :  
  
-   [Types de données &#40;&#41;d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/data-types-data-mining)  
  
-   [Types de contenu &#40;l’exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)  
  
-   [Distributions de colonnes &#40;&#41;d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/column-distributions-data-mining)  
  
-   [Indicateurs de modélisation &#40;&#41;d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/modeling-flags-data-mining)  
  
 Vous pouvez ajouter une clause à l'instruction pour décrire la relation entre deux colonnes. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]prend en charge l’utilisation de \<la clause de> de relation de colonne suivante.  
  
 **EN RAPPORT AVEC**  
 Cette forme indique une hiérarchie des valeurs. La cible d'une colonne RELATED TO peut être une colonne clé dans une table imbriquée, une colonne de valeurs discrètes dans la ligne de cas ou une autre colonne RELATED TO qui indique une hiérarchie plus profonde.  
  
 Utilisez une clause de prévision pour décrire de quelle manière la colonne de prévision est utilisée. Le tableau suivant décrit les deux clauses possibles.  
  
|\<clause de> de prédiction|Description|  
|---------------------------|-----------------|  
|**PREDICT**|Cette colonne peut être prédite par le modèle, et elle peut être fournie à des cas d'entrée pour prédire la valeur d'autres colonnes prédictibles.|  
|**PREDICT_ONLY**|Cette colonne peut être prédite par le modèle, mais ses valeurs ne peuvent pas être utilisées dans des cas d'entrée pour prédire la valeur d'autres colonnes prédictibles.|  
  
### <a name="parameter-definition-list"></a>Liste des définitions des paramètres  
 La liste des paramètres permet d'ajuster les performances et les fonctionnalités d'un modèle d'exploration de données. La syntaxe de la liste des paramètres est la suivante :  
  
```  
[<parameter> = <value>, <parameter> = <value>,...]  
```  
  
 Pour obtenir la liste des paramètres associés à chaque algorithme, consultez [algorithmes d’exploration de données &#40;Analysis Services-exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining).  
  
## <a name="remarks"></a>Notes  
 Si vous souhaitez créer un modèle qui a un jeu de données de test intégré, vous devez utiliser l'instruction CREATE MINING STRUCTURE suivie de ALTER MINING STRUCTURE. Toutefois, les types de modèles ne prennent pas tous en charge un jeu de données d'exclusion. Pour plus d’informations, consultez [CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md).  
  
 Pour obtenir une procédure pas à pas de création d’un modèle d’exploration de données à l’aide de l’instruction CREATEMODEL, consultez le [didacticiel DMX sur la prédiction de série chronologique](https://msdn.microsoft.com/library/38ea7c03-4754-4e71-896a-f68cc2c98ce2).  
  
## <a name="naive-bayes-example"></a>Exemple de modèle Naive Bayes  
 L'exemple suivant utilise l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes pour créer un modèle d'exploration de données. La colonne Bike Buyer (Acheteur de vélo) est définie comme l'attribut prédictible.  
  
```  
CREATE MINING MODEL [NBSample]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE PREDICT  
)  
USING Microsoft_Naive_Bayes  
```  
  
## <a name="association-model-example"></a>Exemple de modèle Association  
 L'exemple suivant utilise l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Association pour créer un modèle d'exploration de données. L'instruction bénéficie de la possibilité d'imbriquer une table dans la définition du modèle en utilisant une colonne de table. Le modèle est modifié à l’aide des paramètres *MINIMUM_PROBABILITY* et *MINIMUM_SUPPORT* .  
  
```  
CREATE MINING MODEL MyAssociationModel (  
    OrderNumber TEXT KEY,  
    [Products] TABLE PREDICT (  
        [Model] TEXT KEY  
    )  
)  
USING Microsoft_Association_Rules (Minimum_Probability = 0.1, MINIMUM_SUPPORT = 0.01)  
```  
  
## <a name="sequence-clustering-example"></a>Exemple de modèle Sequence Clustering  
 L'exemple suivant utilise l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering pour créer un modèle d'exploration de données. Deux clés sont utilisées pour définir le modèle. La colonne OrderNumber est utilisée comme clé de cas et spécifie des commandes individuelles. La colonne LineNumber est utilisée comme clé de table imbriquée et spécifie la séquence selon laquelle les éléments ont été ajoutés à une commande.  
  
```  
CREATE MINING MODEL BuyingSequence (  
    [Order Number] TEXT KEY,  
    [Products] TABLE   
     (  
        [Line Number] LONG KEY SEQUENCE,  
        [Model] TEXT DISCRETE PREDICT  
    )  
)  
USING Microsoft_Sequence_Clustering  
```  
  
## <a name="time-series-example"></a>Exemple de modèle Time Series  
 L'exemple suivant utilise l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series pour créer un modèle d'exploration de données à l'aide de l'algorithme ARTxp. ReportingDate est la colonne clé pour la série chronologique et ModelRegion est la colonne clé pour la série de données. Dans cet exemple, on suppose que la périodicité des données est tous les 12 mois. Par conséquent, le paramètre *PERIODICITY_HINT* a la valeur 12.  
  
> [!NOTE]  
>  Vous devez spécifier le paramètre *PERIODICITY_HINT* à l’aide de caractères d’accolade. En outre, étant donné que la valeur est une chaîne, elle doit être placée entre guillemets simples\<: « {valeur numérique>} ».  
  
```  
CREATE MINING MODEL SalesForecast (  
        ReportingDate DATE KEY TIME,  
        ModelRegion TEXT KEY,  
        Amount LONG CONTINUOUS PREDICT,  
        Quantity LONG CONTINUOUS PREDICT  
)  
USING Microsoft_Time_Series (PERIODICITY_HINT = '{12}', FORECAST_METHOD = 'ARTXP')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
