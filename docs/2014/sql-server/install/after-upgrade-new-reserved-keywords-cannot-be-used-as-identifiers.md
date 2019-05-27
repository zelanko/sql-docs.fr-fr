---
title: Après la mise à niveau, les nouveaux mots clés réservés ne peuvent pas être utilisés comme identificateurs | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- keywords [SQL Server], after upgrade
- keywords [SQL Server], reserved
- keywords [SQL Server]
ms.assetid: cb242081-54f8-4273-a8ef-52f3751c25ef
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d187fbe95a75091b0cbcf4bf09225c5f60a9af01
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66096889"
---
# <a name="after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers"></a>Après une mise à niveau, les nouveaux mots clés réservés ne peuvent pas être utilisés comme identificateurs
  Le Conseiller de mise à niveau a détecté l'utilisation de mots qui sont des mots clés réservés. Un mot clé réservé ne peut pas être utilisé comme un identificateur ou nom d'objet sauf si le nom est délimité.  
  
## <a name="component"></a>Composant  
 Moteur de base de données  
  
## <a name="description"></a>Description  
 Au niveau de compatibilité 90 ou inférieur, les mots suivants ne sont pas des mots clés réservés et peuvent être utilisés comme identificateur ou nom d'objet dans les scripts [!INCLUDE[tsql](../../includes/tsql-md.md)]. Au niveau de compatibilité 100, ces mots sont des mots clé réservés à part entière et ne doivent pas être utilisés comme identificateurs ou noms d'objet.  
  
-   EXTERNAL  
  
-   MERGE  
  
-   PIVOT  
  
-   REVERT  
  
-   STOPLIST  
  
-   TABLESAMPLE  
  
-   UNPIVOT  
  
## <a name="corrective-action"></a>Action corrective  
 Nous vous recommandons de renommer l'objet. Si cette opération ne peut pas être effectuée avant la mise à niveau, utilisez l'une des méthodes suivantes jusqu'à ce que vous puissiez modifier le nom :  
  
-   Conservez la compatibilité de base de données au niveau 90 ou inférieur.  
  
-   Faites référence à l'objet en utilisant des identificateurs délimités. Par exemple, l’instruction `CREATE TABLE [MERGE] ([MERGE] int);` utilise des crochets pour délimiter le nom d’objet MERGE.  
  
## <a name="external-resources"></a>Ressources externes  
 [Reserved Keywords &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql)  
  
 [MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql)  
  
 [Identificateurs délimités (moteur de base de données)](https://go.microsoft.com/fwlink/?LinkId=112509)  
  
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
