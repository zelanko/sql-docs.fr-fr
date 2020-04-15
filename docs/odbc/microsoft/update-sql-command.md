---
title: MISE À JOUR - Commandement SQL Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 818811c18ed52cef5bdb1c4d97f947bb86e67422
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307640"
---
# <a name="update---sql-command"></a>UPDATE, commande SQL
Mise à jour des enregistrements dans un tableau avec de nouvelles valeurs.  
  
 Le Visual FoxPro ODBC Driver prend en charge la syntaxe en langue visuelle FoxPro native pour cette commande. Pour obtenir des renseignements spécifiques au conducteur, consultez **les remarques du conducteur**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>Arguments  
 MISE À JOUR [ *DatabaseName1!*] *TableName1*  
 Spécifie le tableau dans lequel les enregistrements sont mis à jour avec de nouvelles valeurs.  
  
 *DatabaseName1!* spécifie le nom d’une base de données autre que la base de données spécifiée avec la source de données contenant la table. Vous devez inclure le nom de la base de données contenant la table si la base de données n’est pas la base de données actuelle. Inclure le point d’exclamation (!) delimiter après le nom de la base de données et avant le nom de table.  
  
 SET *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Spécifie les colonnes mises à jour et leurs nouvelles valeurs. Si vous ometez la clause WHERE, chaque ligne de la colonne est mise à jour avec la même valeur.  
  
 Où *FilterCondition1*[ET &#124; OU *FilterCondition2*...]  
 Spécifie les enregistrements qui sont mis à jour avec de nouvelles valeurs.  
  
 *FilterCondition* spécifie les critères que les enregistrements doivent respecter pour être mis à jour avec de nouvelles valeurs. Vous pouvez inclure autant de conditions de filtre que vous le souhaitez, les reliant à l’ET ou à l’opérateur OU. Vous pouvez également utiliser l’opérateur PAS pour inverser la valeur d’une expression logique, ou vous pouvez utiliser **EMPTY**( ) pour vérifier un champ vide.  
  
## <a name="remarks"></a>Notes  
 MISE À JOUR - SQL ne peut mettre à jour les enregistrements que dans un seul tableau.  
  
 Contrairement à REPLACE, UPDATE - SQL utilise le verrouillage des enregistrements lors de la mise à jour de plusieurs enregistrements dans des tables ouvertes pour un accès partagé. Cela réduit la contention des records dans les situations multi-autres, mais peut réduire les performances. Pour un maximum de performances, ouvrez la table pour une utilisation exclusive ou utilisez **FLOCK**( ) pour verrouiller la table.  
  
## <a name="driver-remarks"></a>Remarques du conducteur  
 Lorsque votre application envoie la mise À JOUR de relevé SQL ODBC à la source de données, le visual FoxPro ODBC Driver convertit la commande en commande Visual FoxProUPDATE sans traduction.  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE - Commandement SQL](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT, commande SQL](../../odbc/microsoft/insert-sql-command.md)
