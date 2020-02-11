---
title: Créer un repère de plan pour les requêtes paramétrables | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- parameterized queries, plan guides for
- plan guides [SQL Server], parameterized queries
ms.assetid: b532ae16-66e7-4641-9bc8-b0d805853477
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 58202b7246acf2a958523cfb874b8ce25bd13bdc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63150965"
---
# <a name="create-a-plan-guide-for-parameterized-queries"></a>Créer un repère de plan pour les requêtes paramétrables
  Un repère de plan TEMPLATE correspond à des requêtes autonomes paramétrables au format spécifié.  
  
 L'exemple suivant crée un repère de plan correspondant à la requête qui paramètre selon une forme donnée, et commande à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'imposer le paramétrage de la requête. La syntaxe des deux requêtes suivantes est équivalente, seules leurs valeurs littérales constantes diffèrent.  
  
```  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45639;  
  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45640;  
```  
  
 Voici le repère de plan pour la forme paramétrable de la requête :  
  
```  
EXEC sp_create_plan_guide   
    @name = N'TemplateGuide1',  
    @stmt = N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
              INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
                  ON h.SalesOrderID = d.SalesOrderID  
              WHERE h.SalesOrderID = @0',  
    @type = N'TEMPLATE',  
    @module_or_batch = NULL,  
    @params = N'@0 int',  
    @hints = N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 Dans l'exemple précédent, la valeur du paramètre `@stmt` correspond à la forme paramétrable de la requête. La procédure stockée système [sp_get_query_template](/sql/relational-databases/system-stored-procedures/sp-get-query-template-transact-sql) est la seule méthode fiable pour obtenir cette valeur et pouvoir l’utiliser dans sp_create_plan_guide. Vous pouvez utiliser le script suivant à la fois pour obtenir la requête paramétrable et créer ensuite un repère de plan à partir de celle-ci.  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
      INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
          ON h.SalesOrderID = d.SalesOrderID  
      WHERE h.SalesOrderID = 45639;',  
    @stmt OUTPUT,   
    @params OUTPUT  
EXEC sp_create_plan_guide N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
> [!IMPORTANT]  
>  Les valeurs littérales constantes du paramètre `@stmt` transmises à `sp_get_query_template` peuvent affecter le type de données choisi pour le paramètre qui remplace le littéral. Ceci va également affecter la mise en correspondance du repère de plan. Vous devrez peut-être créer plusieurs repères de plan pour traiter plusieurs plages de valeurs.  
  
 Vous pouvez combiner les repères de plan TEMPLATE et les repères de plan SQL. Ainsi, vous pouvez créer un repère de plan TEMPLATE pour vous assurer qu'une classe de requêtes est paramétrable, et ensuite créer un repère de plan SQL sur la forme paramétrable de cette requête.  
  
  
