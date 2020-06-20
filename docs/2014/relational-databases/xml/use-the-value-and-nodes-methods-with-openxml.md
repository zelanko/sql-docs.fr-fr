---
title: Utiliser les méthodes value() et nodes() avec OPENXML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- OpenXML method [XML in SQL Server]
- value method [XML in SQL Server]
- nodes method [XML in SQL Server]
ms.assetid: c73dbe55-d685-42eb-b0ee-9f3c5b9d97f3
author: rothja
ms.author: jroth
ms.openlocfilehash: d63a3ebc13f5bfc0852c589a36185b5147c8c8d0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061169"
---
# <a name="use-the-value-and-nodes-methods-with-openxml"></a>Utiliser les méthodes value() et nodes() avec OPENXML
  Vous pouvez utiliser plusieurs méthodes **value ()** sur le `xml` type de données dans une clause **Select** pour générer un ensemble de lignes de valeurs extraites. La méthode **nodes()** produit une référence interne pour chaque nœud sélectionné en vue d’une requête supplémentaire. La combinaison des méthodes **nodes()** et **value()** peut s’avérer plus efficace pour générer l’ensemble de lignes quand il contient plusieurs colonnes et, peut-être, quand les expressions de chemin utilisées durant sa génération sont complexes.  
  
 La méthode **Nodes ()** génère des instances d’un `xml` type de données spécial, chacune ayant son contexte défini sur un nœud sélectionné différent. Ce genre d’instance XML prend en charge les méthodes **query()** , **value()** , **nodes()** et **exist()** , et peut être utilisé dans les agrégations **count(\*)** . Tous les autres emplois génèrent une erreur.  
  
## <a name="example-using-nodes"></a>Exemple : utilisation de nodes()  
 Supposez que vous voulez extraire les prénoms et les noms des auteurs et que le premier prénom ne soit pas « David ». En outre, vous voulez extraire ces informations sous forme d'un ensemble de lignes composé de deux colonnes, FirstName et LastName. En utilisant les méthodes **nodes()** et **value()** , vous pouvez y parvenir en procédant ainsi :  
  
```  
SELECT nref.value('(first-name/text())[1]', 'nvarchar(50)') FirstName,  
       nref.value('(last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T CROSS APPLY xCol.nodes('//author') AS R(nref)  
WHERE  nref.exist('first-name[. != "David"]') = 1  
```  
  
 Dans cet exemple, `nodes('//author')` génère un ensemble de lignes de références aux éléments `<author>` pour chaque instance XML. Les prénoms et noms des auteurs sont obtenus en évaluant les méthodes **value()** relatives à ces références.  
  
 Avec SQL Server 2000, vous avez la possibilité de générer un ensemble de lignes à partir d’une instance XML en utilisant **OpenXml()** . Vous pouvez spécifier le schéma relationnel pour l'ensemble de lignes et la façon de mapper les valeurs de l'instance XML avec les colonnes de l'ensemble de lignes.  
  
## <a name="example-using-openxml-on-the-xml-data-type"></a>Exemple : utilisation de OpenXml() sur le type de données xml  
 La requête peut être réécrite d’après l’exemple précédent en utilisant **OpenXml()** , comme le montre l’exemple suivant. Vous devez pour cela créer un curseur qui lit chaque instance XML dans une variable XML, et y applique ensuite OpenXML :  
  
```  
DECLARE name_cursor CURSOR  
FOR  
   SELECT xCol   
   FROM   T  
OPEN name_cursor  
DECLARE @xmlVal XML  
DECLARE @idoc int  
FETCH NEXT FROM name_cursor INTO @xmlVal  
  
WHILE (@@FETCH_STATUS = 0)  
BEGIN  
   EXEC sp_xml_preparedocument @idoc OUTPUT, @xmlVal  
   SELECT   *  
   FROM   OPENXML (@idoc, '//author')  
          WITH (FirstName  varchar(50) 'first-name',  
                LastName   varchar(50) 'last-name') R  
   WHERE  R.FirstName != 'David'  
  
   EXEC sp_xml_removedocument @idoc  
   FETCH NEXT FROM name_cursor INTO @xmlVal  
END  
CLOSE name_cursor  
DEALLOCATE name_cursor   
```  
  
 La fonction**OpenXml()** crée une représentation en mémoire et utilise les tables de travail plutôt que le processeur de requêtes. Elle s'appuie ensuite sur le processeur XPath version 1.0 de MSXML version 3.0 au lieu du moteur XQuery. Les tables de travail ne sont plus partagées entre plusieurs appels à **OpenXml()** , même s’il s’agit de la même instance XML. L'évolutivité est ainsi limitée. La fonction**OpenXml()** vous permet d’accéder à un format de table edge pour les données XML quand la clause WITH n’est pas spécifiée. De plus, vous pouvez utiliser la valeur XML restante dans une colonne distincte réservée aux données en excès.  
  
 La combinaison des fonctions **nodes()** et **value()** tire pleinement parti des index XML. Cette combinaison montre donc une plus grande capacité d'évolution que **OpenXml**.  
  
## <a name="see-also"></a>Voir aussi  
 [OPENXML &#40;SQL Server&#41;](openxml-sql-server.md)  
  
  
