---
title: Spécifier le comportement du paramétrage de requêtes grâce aux repères de plan | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- PARAMETERIZATION FORCED option
- PARAMETERIZATION option
- PARAMETERIZATION SIMPLE option
- parameterization [SQL Server]
- overriding parameterization behavior
- plan guides [SQL Server], parameterization
- parameterized queries [SQL Server]
ms.assetid: f0f738ff-2819-4675-a8c8-1eb6c210a7e6
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 06ed5433d23501016a0ea308c9238fcf7bc1b3c1
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582064"
---
# <a name="specify-query-parameterization-behavior-by-using-plan-guides"></a>Spécifier le comportement du paramétrage de requêtes grâce aux repères de plan
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Si l'option de base de données PARAMETERIZATION a la valeur SIMPLE, il se peut que l'optimiseur de requête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] opte pour le paramétrage des requêtes. En d'autres termes, toute valeur littérale contenue dans une requête est substituée par des paramètres. Ce processus s'appelle le paramétrage simple. Lorsque le paramétrage SIMPLE s'applique, vous ne pouvez pas décider des requêtes devant être paramétrables et de celles ne devant pas l'être. Vous pouvez cependant indiquer que toutes les requêtes d'une base de données soient paramétrables en affectant à l'option de base de données PARAMETERIZATION la valeur FORCED. Ce processus s'appelle le paramétrage forcé.  
  
 Vous pouvez outrepasser ce comportement de paramétrage d'une base de données par le biais de repères de plan des façons suivantes :  
  
-   Quand l'option de base de données PARAMETERIZATION a la valeur SIMPLE, vous pouvez spécifier que le paramétrage forcé doit être tenté sur une certaine classe de requêtes. Pour ce faire, créez un repère de plan TEMPLATE sur la forme paramétrable de la requête et spécifiez l’indicateur de requête PARAMETERIZATION FORCED dans la procédure stockée [sp_create_plan_guide](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md) . Ce type de repère de plan peut être considéré comme un moyen de forcer le paramétrage sur une classe de requêtes seulement plutôt que sur toutes les requêtes.  
  
-   Quand l'option de base de données PARAMETERIZATION a la valeur FORCED, vous pouvez spécifier que, pour une certaine classe de requêtes, seul un paramétrage simple est tenté, et non pas un paramétrage forcé. Pour ce faire, créez un repère de plan TEMPLATE sur la forme avec paramétrage forcé de la requête et spécifiez l’indicateur de requête PARAMETERIZATION SIMPLE dans la procédure stockée **sp_create_plan_guide**.  
  
 Supposons la requête suivante portant sur la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] :  
  
```  
SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
FROM Production.ProductModel AS pm   
    INNER JOIN Production.ProductInventory AS pi   
        ON pm.ProductModelID = pi.ProductID   
WHERE pi.ProductID = 101   
GROUP BY pi.ProductID, pi.Quantity HAVING SUM(pi.Quantity) > 50;  
```  
  
 Vous pouvez choisir de ne pas activer le paramétrage forcé de toutes les requêtes portant sur la base de données à condition d'en être l'administrateur. En revanche, vous voulez éviter les coûts de compilation sur toutes les requêtes équivalentes dans leur syntaxe à la requête précédente, mais différant sur leurs valeurs littérales constantes uniquement. En d'autres termes, il peut être préférable que la requête soit paramétrable afin qu'un plan de requête correspondant à ce type de requête soit réutilisé. Dans ce cas, suivez les étapes ci-dessous :  
  
1.  Récupérez la forme paramétrable de la requête. La seule méthode sûre pour obtenir cette valeur et l’utiliser dans la procédure stockée **sp_create_plan_guide** consiste à passer par la procédure stockée système [sp_get_query_template](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md) .  
  
2.  Créez le repère de plan sur la forme paramétrable de la requête en spécifiant l'indicateur de requête PARAMETERIZATION FORCED.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    > [!IMPORTANT]  
    >  As part of parameterizing a query, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns a data type to the parameters that replace the literal values, depending on the value and size of the literal. The same process occurs to the value of the constant literals passed to the **@stmt** output parameter of **sp_get_query_template**. Because the data type specified in the **@params** argument of **sp_create_plan_guide** must match that of the query as it is parameterized by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you may have to create more than one plan guide to cover the complete range of possible parameter values for the query.  
  
 Le script suivant peut être utilisé aussi bien pour obtenir la requête paramétrable que pour créer plus tard un repère de plan s'y rapportant :  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total   
      FROM Production.ProductModel AS pm   
      INNER JOIN Production.ProductInventory AS pi ON pm.ProductModelID = pi.ProductID   
      WHERE pi.ProductID = 101   
      GROUP BY pi.ProductID, pi.Quantity   
      HAVING sum(pi.Quantity) > 50',  
    @stmt OUTPUT,   
    @params OUTPUT;  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 De même, dans une base de données où le paramétrage forcé est déjà activé, vous pouvez vous assurer que la requête donnée en exemple et celles dont la syntaxe est équivalente, sauf pour leurs valeurs littérales constantes, sont paramétrables selon les règles du paramétrage simple. Pour ce faire, spécifiez PARAMETERIZATION SIMPLE plutôt que PARAMETERIZATION FORCED dans la clause OPTION.  
  
> [!NOTE]  
>  Les repères de plan TEMPLATE font correspondre les instructions aux requêtes envoyées par traitements qui sont composées d'une seule instruction. Les instructions à l'intérieur de traitements à instructions multiples ne peuvent pas être mises en correspondance avec les repères de plan TEMPLATE.  
  
  
