---
title: "Commande de mise à jour - SQL | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: update [ODBC]
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6fb2e4d3e3010eaba53b36de383c3365d82db289
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="update---sql-command"></a>Commande de mise à jour - SQL
Met à jour des enregistrements dans une table avec les nouvelles valeurs.  
  
 Le pilote ODBC Visual FoxPro prend en charge la syntaxe du langage Visual FoxPro native pour cette commande. Pour plus d’informations spécifiques au pilote, consultez **pilote notes**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>Arguments  
 Mise à jour [ *DatabaseName1 !*] *TableName1*  
 Spécifie la table dans laquelle des enregistrements sont mis à jour avec de nouvelles valeurs.  
  
 *DatabaseName1 !* Spécifie le nom d’une base de données autre que la base de données spécifiée avec la source de données contenant la table. Vous devez inclure le nom de la base de données contenant la table si la base de données n’est pas celle en cours. Inclure le séparateur de point d’exclamation ( !) après le nom de la base de données et avant le nom de table.  
  
 Définissez *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Spécifie les colonnes qui sont mises à jour et leurs nouvelles valeurs. Si vous omettez la clause WHERE, chaque ligne dans la colonne est mise à jour avec la même valeur.  
  
 OÙ *FilterCondition1*[AND &#124; OU *FilterCondition2*...]  
 Spécifie les enregistrements sont mis à jour avec de nouvelles valeurs.  
  
 *FilterCondition* spécifie les critères que les enregistrements doivent respecter pour être mis à jour avec de nouvelles valeurs. Vous pouvez inclure autant de conditions de filtre que vous le souhaitez, qui les connectent avec AND ou opérateur OR. Vous pouvez également utiliser l’opérateur NOT pour inverser la valeur d’une expression logique, ou vous pouvez utiliser **vide**() pour rechercher un champ vide.  
  
## <a name="remarks"></a>Notes   
 Mise à jour - SQL peut mettre à jour uniquement les enregistrements dans une table unique.  
  
 Contrairement à remplacer, mise à jour - SQL utilise le verrouillage lors de la mise à jour de plusieurs enregistrements dans les tables ouvert pour l’accès partagé. Cela réduit la contention enregistrement dans les situations multi-utilisateur, mais peut réduire les performances. Pour optimiser les performances, ouvrez la table d’exclusive utilisez ou **généalogique**() pour verrouiller la table.  
  
## <a name="driver-remarks"></a>Section Notes de pilote  
 Lorsque votre application envoie l’instruction SQL ODBC mise à jour à la source de données, le pilote ODBC Visual FoxPro convertit la commande dans la commande Visual FoxProUPDATE sans traduction.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer : la commande SQL](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT, commande SQL](../../odbc/microsoft/insert-sql-command.md)
