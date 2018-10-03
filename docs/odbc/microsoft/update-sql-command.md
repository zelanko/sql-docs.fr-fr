---
title: Commande de mise à jour - SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- update [ODBC]
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3fbd5ec98791d782fe7ad1fdb1e1884b646dcf9f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818307"
---
# <a name="update---sql-command"></a>UPDATE, commande SQL
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
  
 *DatabaseName1 !* Spécifie le nom d’une base de données autre que la base de données spécifié avec la source de données contenant la table. Vous devez inclure le nom de la base de données contenant la table si la base de données n’est pas celui en cours. Inclure le séparateur de point d’exclamation ( !) après le nom de la base de données et avant le nom de table.  
  
 Définissez *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Spécifie les colonnes qui sont mises à jour et leurs nouvelles valeurs. Si vous omettez la clause WHERE, chaque ligne dans la colonne est mise à jour avec la même valeur.  
  
 OÙ *FilterCondition1*[AND &#124; ou *FilterCondition2*...]  
 Spécifie les enregistrements sont mis à jour avec de nouvelles valeurs.  
  
 *FilterCondition* spécifie les critères que les enregistrements doivent satisfaire pour être mis à jour avec de nouvelles valeurs. Vous pouvez inclure autant de conditions de filtre que vous le souhaitez, connectant à l’opération AND ou opérateur OR. Vous pouvez également utiliser l’opérateur NOT pour inverser la valeur d’une expression logique, ou vous pouvez utiliser **vide**() pour rechercher un champ vide.  
  
## <a name="remarks"></a>Notes  
 Mise à jour - SQL peut mettre à jour uniquement les enregistrements dans une table unique.  
  
 Contrairement à remplacer, mise à jour - SQL utilise le verrouillage des enregistrements lorsque la mise à jour plusieurs enregistrements dans les tables ouvert pour un accès partagé. Cela réduit la contention enregistrement dans les situations multi-utilisateur, mais peut réduire les performances. Pour optimiser les performances, ouvrez la table d’exclusive utilisez ou **troupeau**() pour verrouiller la table.  
  
## <a name="driver-remarks"></a>Notes de pilote  
 Lorsque votre application envoie l’instruction SQL ODBC mise à jour à la source de données, le pilote ODBC Visual FoxPro convertit la commande dans la commande FoxProUPDATE Visual sans traduction.  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, commande SQL](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT, commande SQL](../../odbc/microsoft/insert-sql-command.md)
