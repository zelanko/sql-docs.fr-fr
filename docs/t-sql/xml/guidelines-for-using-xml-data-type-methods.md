---
title: "Instructions d’utilisation des méthodes de Type de données xml | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- xml data type [SQL Server], methods
- methods [XML in SQL Server]
ms.assetid: 1a483aa1-42de-4c88-a4b8-c518def3d496
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f22c3535c66663979009d1e760ecf8c2164bc765
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="guidelines-for-using-xml-data-type-methods"></a>Instructions pour l'utilisation des méthodes de type de données XML
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Cette rubrique décrit comment utiliser le **xml** méthodes du type de données.  
  
## <a name="the-print-statement"></a>Instruction PRINT  
 Le **xml** méthodes de type de données ne peut pas être utilisés dans l’instruction PRINT, comme indiqué dans l’exemple suivant. Le **xml** méthodes de type de données sont traitées comme des sous-requêtes et les sous-requêtes ne sont pas autorisées dans l’instruction PRINT. Par conséquent, l'exemple ci-dessous retourne une erreur :  
  
```  
DECLARE @x xml  
SET @x = '<root>Hello</root>'  
PRINT @x.value('/root[1]', 'varchar(20)') -- will not work because this is treated as a subquery (select top 1 col from table)   
```  
  
 Une solution consiste à attribuer le résultat de la **value()** méthode à une variable de **xml** tapez, puis spécifiez la variable dans la requête.  
  
```  
DECLARE @x xml  
DECLARE @c varchar(max)  
SET @x = '<root>Hello</root>'  
SET @c = @x.value('/root[1]', 'varchar(11)')  
PRINT @c                                                        
```  
  
## <a name="the-group-by-clause"></a>Clause GROUP BY  
 Le **xml** méthodes de type de données sont traitées en interne comme des sous-requêtes. Étant donné que GROUP BY requiert une valeur scalaire et n’autorise pas les agrégats et les sous-requêtes, vous ne pouvez pas spécifier le **xml** méthodes de type de données dans la clause GROUP BY. Une solution consiste à appeler une fonction définie par l'utilisateur qui utilise des méthodes XML en son sein.  
  
## <a name="reporting-errors"></a>Signalement des erreurs  
 En cas de signalement d’erreurs, **xml** méthodes de type de données génèrent une erreur unique au format suivant :  
  
```  
Msg errorNumber, Level levelNumber, State stateNumber:  
XQuery [database.table.method]: description_of_error  
```  
  
 Exemple :  
  
```  
Msg 2396, Level 16, State 1:  
XQuery [xmldb_test.xmlcol.query()]: Attribute may not appear outside of an element  
```  
  
## <a name="singleton-checks"></a>Vérifications des singletons  
 Les étapes d'emplacement, les paramètres de fonction et les opérateurs qui réclament des singletons renverront une erreur lorsque le compilateur n'arrive pas à savoir si la présence d'un singleton est garantie lors de l'exécution. Ce problème se produit souvent avec des données non typées. Par exemple, la recherche d'un attribut exige un élément parent unique. Un nombre ordinal qui sélectionne un nœud parent unique suffit. L’évaluation d’une **node()**-**value()** combinaison pour extraire les valeurs d’attribut peuvent ne pas nécessite la spécification ordinale. comme le montre l'exemple suivant.  
  
### <a name="example-known-singleton"></a>Exemple : Singleton connu  
 Dans cet exemple, le **nodes()** méthode génère une ligne distincte pour chaque <`book`> élément. Le **value()** méthode qui est évaluée sur un <`book`> nœud extrait la valeur de @genre et un attribut, est un singleton.  
  
```  
SELECT nref.value('@genre', 'varchar(max)') LastName  
FROM   T CROSS APPLY xCol.nodes('//book') AS R(nref)  
```  
  
 Le schéma XML sert à vérifier le type en cas de code XML typé. Si un nœud est spécifié en tant que singleton dans le schéma XML, le compilateur utilise cette information et aucune erreur ne se produit. Dans le cas contraire, un nombre ordinal sélectionnant un nœud unique est requis. En particulier, l’utilisation de l’axe descendant-or-self (/ /) axe, comme dans/book / / title, perd l’inférence de cardinalité de singleton pour le \<titre > élément, même si le schéma XML spécifie pour être. Vous devez par conséquent le réécrire sous la forme (/book//title)[1].  
  
 Il faut toujours garder à l'esprit la différence qui existe entre //first-name[1] et (//first-name)[1] en cas de vérification du type. Le premier retourne une séquence de \<first-name > nœuds dans lequel chaque nœud est le plus à gauche \<first-name > nœud parmi ses frères. Ce dernier renvoie la première singleton \<first-name > nœud dans l’ordre du document dans l’instance XML.  
  
### <a name="example-using-value"></a>Exemple : Utilisation de value()  
 La requête suivante sur une colonne XML non typée entraîne une erreur de compilation statique. C’est parce que **value()** attend un nœud singleton comme premier argument et le compilateur ne peut pas déterminer si seul \<last-name > nœud se produit au moment de l’exécution :  
  
```  
SELECT xCol.value('//author/last-name', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 L'exemple suivant vous montre une solution à envisager :  
  
```  
SELECT xCol.value('//author/last-name[1]', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 Toutefois, cette solution ne permet pas de remédier à l'erreur car il peut y avoir plusieurs nœuds <`author`> dans chaque instance XML. Réécrit ainsi, l'exemple fonctionne :  
  
```  
SELECT xCol.value('(//author/last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T  
```  
  
 Cette requête renvoie la valeur du premier élément `<last-name>` de chaque instance XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)  
  
  
