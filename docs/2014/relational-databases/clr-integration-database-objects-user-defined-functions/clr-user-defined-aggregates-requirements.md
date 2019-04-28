---
title: Configuration requise pour les agrégats CLR définis par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- user-defined types [CLR integration], user-defined aggregates
- CREATE AGGREGATE statement
- SqlUserDefinedAggregate attribute
- aggregate methods [CLR integration]
- assemblies [CLR integration], user-defined aggregate functions
- custom aggregates [CLR integration]
- user-defined functions [CLR integration]
- UDTs [CLR integration], user-defined aggregates
ms.assetid: dbf9eb5a-bd99-42f7-b275-556d0def045d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 31b22b1dce53bb82f85ae946290024408d2facd3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874481"
---
# <a name="requirements-for-clr-user-defined-aggregates"></a>Conditions requises pour les agrégats CLR définis par l'utilisateur
  Un type dans un assembly CLR (Common Language Runtime) peut être enregistré comme une fonction d'agrégation définie par l'utilisateur, tant qu'il implémente le contrat d'agrégation requis. Ce contrat se compose de l'attribut `SqlUserDefinedAggregate` et des méthodes du contrat d'agrégation. Le contrat d'agrégation inclut le mécanisme permettant d'enregistrer l'état intermédiaire de l'agrégation, ainsi que le mécanisme permettant d'accumuler de nouvelles valeurs, lequel est composé de quatre méthodes : `Init`, `Accumulate`, `Merge` et `Terminate`. Lorsque ces conditions sont satisfaites, vous serez en mesure de tirer pleinement parti des agrégats définis par l’utilisateur dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les sections suivantes de cette rubrique fournissent des détails supplémentaires sur la façon de créer et d'utiliser les agrégats définis par l'utilisateur. Pour obtenir un exemple, consultez [Invoking CLR User-Defined les fonctions d’agrégation](clr-user-defined-aggregate-invoking-functions.md).  
  
## <a name="sqluserdefinedaggregate"></a>SqlUserDefinedAggregate  
 Pour plus d’informations, consultez [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="aggregation-methods"></a>Méthodes d'agrégation  
 La classe inscrite comme agrégat défini par l'utilisateur doit prendre en charge les méthodes d'instance suivantes. Ce sont les méthodes que le processeur de requêtes utilise pour calculer l'agrégation :  
  
|Méthode|Syntaxe|Description|  
|------------|------------|-----------------|  
|`Init`|public void Init();|Le processeur de requêtes utilise cette méthode pour initialiser le calcul de l'agrégation. Cette méthode est appelée une fois pour chaque groupe dont le processeur de requêtes effectue l'agrégation. Le processeur de requêtes peut choisir de réutiliser la même instance de la classe d'agrégation pour calculer des agrégats de plusieurs groupes. La méthode `Init` doit effectuer tout nettoyage nécessaire à partir des utilisations précédentes de cette instance et lui permettre de redémarrer un nouveau calcul d'agrégation.|  
|`Accumulate`|public Accumulate void (valeur de type d’entrée [, valeur de type d’entrée,...]) ;|Un ou plusieurs paramètres représentant les paramètres de la fonction. *INPUT_TYPE* doit être managé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données équivalent natif [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données spécifié par *input_sqltype* dans le `CREATE AGGREGATE` instruction. Pour plus d’informations, consultez [mappage des données de paramètre CLR](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).<br /><br /> Pour les types définis par l'utilisateur (UDT), le type d'entrée est le même que le type UDT. Le processeur de requêtes utilise cette méthode pour accumuler les valeurs d'agrégation. La méthode est appelée une fois pour chaque valeur dans le groupe qui fait l'objet de l'agrégation. Le processeur de requêtes l'appelle uniquement après avoir appelé la méthode `Init` sur l'instance donnée de la classe d'agrégation. L'implémentation de cette méthode doit mettre à jour l'état de l'instance pour refléter l'accumulation de la valeur d'argument qui est passée.|  
|`Merge`|Fusion void publique (valeur udagg_class) ;|Cette méthode peut être utilisée pour fusionner une autre instance de cette classe d'agrégation avec l'instance actuelle. Le processeur de requêtes utilise cette méthode pour fusionner plusieurs calculs partiels d'une agrégation.|  
|`Terminate`|return_type publique utiliser Terminate() ;|Cette méthode termine le calcul d'agrégation et retourne le résultat de l'agrégation. Le *return_type* doit être managé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de type de données qui est l’équivalent managé de *return_sqltype* spécifié dans le `CREATE AGGREGATE` instruction. Le *return_type* peut également être un type défini par l’utilisateur.|  
  
### <a name="table-valued-parameters"></a>Paramètres table  
 Les paramètres table (types de tables définis par l'utilisateur et passés dans une procédure ou une fonction) offrent un moyen efficace pour passer plusieurs lignes de données au serveur. Ils procurent une fonctionnalité semblable aux tableaux de paramètres, mais offrent une meilleure souplesse et une intégration plus étroite à [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ils sont également susceptibles de générer de meilleures performances. Les paramètres table aident également à réduire le nombre d'allers-retours au serveur. Au lieu d'envoyer plusieurs demandes au serveur, comme avec une liste de paramètres scalaires, les données peuvent être envoyées au serveur en tant que paramètres table. Un type de table défini par l'utilisateur ne peut pas être passé en tant que paramètre table à une fonction ou à une procédure stockée managée s'exécutant dans le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ni être retourné à partir de ces dernières. Également, les paramètres table ne peuvent pas être utilisés dans l'étendue d'une connexion contextuelle. Toutefois, un paramètre table peut être utilisé avec SqlClient dans les procédures stockées managées ou les fonctions qui exécutent dans le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], s'il est utilisé dans une connexion qui n'est pas une connexion contextuelle. La connexion peut s'effectuer au serveur qui exécute la procédure managée ou la fonction. Pour plus d’informations sur les paramètres table, consultez [utiliser les paramètres &#40;moteur de base de données&#41;](../tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|Mise à jour de la description de la méthode `Accumulate` qui accepte à présent plusieurs paramètres.|  
  
## <a name="see-also"></a>Voir aussi  
 [Types CLR définis par l’utilisateur](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Appel de fonctions d’agrégation CLR définies par l’utilisateur](clr-user-defined-aggregate-invoking-functions.md)  
  
  
