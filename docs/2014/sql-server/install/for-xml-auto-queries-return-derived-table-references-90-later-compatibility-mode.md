---
title: Les requêtes FOR XML AUTO retournent des références de tables dérivées dans les modes de compatibilité 90 ou ultérieur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FOR XML AUTO [SQL Server]
ms.assetid: 10c32f06-f7e1-40e0-8f79-6d921f2bef1d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5b42d8fd7694aaa3962d049cb0e9663479778958
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66095188"
---
# <a name="for-xml-auto-queries-return-derived-table-references-in-90-or-later-compatibility-modes"></a>Les requêtes FOR XML AUTO retournent des références de tables dérivées en mode de compatibilité 90 ou ultérieur
  Lorsque le niveau de compatibilité de la base de données est supérieur ou égal à 90, les requêtes FOR XML qui s'exécutent en mode AUTO retournent des références à des alias de table dérivée. Lorsque le niveau de compatibilité est égal à 80, les instructions FOR XML AUTO retournent des références à des tables de base qui définissent une table dérivée.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Imaginons, par exemple, la table suivante :  
  
```  
CREATE TABLE Test(id int);  
INSERT INTO Test VALUES(1);  
INSERT INTO Test VALUES(2);  
```  
  
 La requête suivante, qui inclut une table dérivée, produit des résultats différents lorsque le niveau de comptabilité est égal à 80, 90 ou une valeur supérieure :  
  
```  
SELECT * FROM   
   (SELECT a.id AS a, b.id AS b   
    FROM Test a JOIN Test b ON a.id=b.id)  
AS DerivedTest   
FOR XML AUTO;  
```  
  
 Lorsque le niveau de compatibilité est égal à 80, la requête retourne les résultats suivants. Les résultats référencent les alias des tables de base `a` et `b` de la table dérivée au lieu de l'alias de la table dérivée.  
  
```  
<a a="1"><b b="1"/></a><a a="2"><b b="2"/></a>  
```  
  
 Lorsque le niveau de compatibilité est supérieur ou égal à 90, la requête retourne des références à l'alias de la table dérivée `DerivedTest` au lieu de références aux tables de base de la table dérivée.  
  
```  
<DerivedTest a="1" b="1"/><DerivedTest a="2" b="2"/>  
```  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez votre application comme il convient pour prendre en compte les modifications dans les résultats des requêtes FOR XML AUTO qui incluent des tables dérivées et qui s'exécutent avec un niveau de compatibilité supérieur ou égal à 90.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
