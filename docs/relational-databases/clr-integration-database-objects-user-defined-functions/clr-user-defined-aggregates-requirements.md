---
title: Exigences pour les agrégats définis par l’utilisateur CLR (fr) Microsoft Docs
description: L’intégration SQL Server CLR vous permet de créer des fonctions agrégées personnalisées dans le code géré. Ils doivent mettre en œuvre le contrat d’agrégation requis.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
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
ms.openlocfilehash: 9dd27cf3751400d3902ddd4199daee8aeef78b80
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487935"
---
# <a name="clr-user-defined-aggregates---requirements"></a>Agrégats CLR définis par l’utilisateur - Exigences
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Un type dans un assembly CLR (Common Language Runtime) peut être enregistré comme une fonction d'agrégation définie par l'utilisateur, tant qu'il implémente le contrat d'agrégation requis. Ce contrat se compose de l’attribut **SqlUserDefinedAggregate** et des méthodes de contrat d’agrégation. Le contrat d’agrégation comprend le mécanisme pour sauver l’état intermédiaire de l’agrégation, et le mécanisme d’accumulation de nouvelles valeurs, qui se compose de quatre méthodes: **Init**, **Accumuler**, **fusionner**, et **terminer**. Lorsque vous avez satisfait à ces exigences, vous serez en mesure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de tirer pleinement parti des agrégats définis par l’utilisateur dans . Les sections suivantes de cette rubrique fournissent des détails supplémentaires sur la façon de créer et d'utiliser les agrégats définis par l'utilisateur. Par exemple, voir [Invoquant CLR Fonctions agrégées définies par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md).  
  
## <a name="sqluserdefinedaggregate"></a>SqlUserDefinedAggregate  
 Pour plus d’informations, voir [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="aggregation-methods"></a>Méthodes d'agrégation  
 La classe inscrite comme agrégat défini par l'utilisateur doit prendre en charge les méthodes d'instance suivantes. Ce sont les méthodes que le processeur de requêtes utilise pour calculer l'agrégation :  
  
|Méthode|Syntaxe|Description|  
|------------|------------|-----------------|  
|**Init**|`public void Init();`|Le processeur de requêtes utilise cette méthode pour initialiser le calcul de l'agrégation. Cette méthode est appelée une fois pour chaque groupe dont le processeur de requêtes effectue l'agrégation. Le processeur de requêtes peut choisir de réutiliser la même instance de la classe d'agrégation pour calculer des agrégats de plusieurs groupes. La méthode **Init** doit effectuer tout nettoyage au besoin à partir d’utilisations précédentes de cette instance, et lui permettre de relancer un nouveau calcul d’agrégats.|  
|**Accumuler**|`public void Accumulate ( input-type value[, input-type value, ...]);`|Un ou plusieurs paramètres représentant les paramètres de la fonction. *input_type* devrait être le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gérées équivalent au type de données native spécifié par *input_sqltype* dans l’énoncé **CREATE AGGREGATE.** Pour plus d’informations, voir [Mapping CLR Parameter Data](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).<br /><br /> Pour les types définis par l'utilisateur (UDT), le type d'entrée est le même que le type UDT. Le processeur de requêtes utilise cette méthode pour accumuler les valeurs d'agrégation. La méthode est appelée une fois pour chaque valeur dans le groupe qui fait l'objet de l'agrégation. Le processeur de requête appelle toujours cela seulement après avoir appelé la méthode **Init** sur l’exemple donné de la classe globale. L'implémentation de cette méthode doit mettre à jour l'état de l'instance pour refléter l'accumulation de la valeur d'argument qui est passée.|  
|**Fusionner**|`public void Merge( udagg_class value);`|Cette méthode peut être utilisée pour fusionner une autre instance de cette classe d'agrégation avec l'instance actuelle. Le processeur de requêtes utilise cette méthode pour fusionner plusieurs calculs partiels d'une agrégation.|  
|**Terminate**|`public return_type Terminate();`|Cette méthode termine le calcul d'agrégation et retourne le résultat de l'agrégation. Le *return_type* devrait être un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données gérée qui est l’équivalent géré de *return_sqltype* spécifié dans l’énoncé **CREATE AGGREGATE.** Le *return_type* peut également être un type défini par l’utilisateur.|  
  
### <a name="table-valued-parameters"></a>Paramètres table  
 Les paramètres table (types de tables définis par l'utilisateur et passés dans une procédure ou une fonction) offrent un moyen efficace pour passer plusieurs lignes de données au serveur. Ils procurent une fonctionnalité semblable aux tableaux de paramètres, mais offrent une meilleure souplesse et une intégration plus étroite à [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ils sont également susceptibles de générer de meilleures performances. Les paramètres table aident également à réduire le nombre d'allers-retours au serveur. Au lieu d'envoyer plusieurs demandes au serveur, comme avec une liste de paramètres scalaires, les données peuvent être envoyées au serveur en tant que paramètres table. Un type de table défini par l'utilisateur ne peut pas être passé en tant que paramètre table à une fonction ou à une procédure stockée managée s'exécutant dans le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ni être retourné à partir de ces dernières. Également, les paramètres table ne peuvent pas être utilisés dans l'étendue d'une connexion contextuelle. Toutefois, un paramètre table peut être utilisé avec SqlClient dans les procédures stockées managées ou les fonctions qui exécutent dans le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], s'il est utilisé dans une connexion qui n'est pas une connexion contextuelle. La connexion peut s'effectuer au serveur qui exécute la procédure managée ou la fonction. Pour plus d’informations sur les TVP, voir [Utilisez les paramètres évalués par la table &#40;moteur de base de données&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|Mise à jour de la description de la méthode **Accumulate;** il accepte maintenant plus d’un paramètre.|  
  
## <a name="see-also"></a>Voir aussi  
 [Types définis par l’utilisateur CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Appel de fonctions d'agrégation CLR définies par l'utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
  
  
