---
title: 'Supprimer : la commande SQL | Documents Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea0b09d77b6d2df8ddd525df17526573b6a1e1be
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="delete---sql-command"></a>Supprimer : la commande SQL
Marque les enregistrements marqués en suppression.  
  
 Le pilote ODBC Visual FoxPro prend en charge la syntaxe du langage Visual FoxPro native pour cette commande. Pour plus d’informations spécifiques au pilote, consultez la section Notes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>Arguments  
 À partir de [ *DatabaseName !*] *TableName*  
 Spécifie la table dans laquelle les enregistrements sont marqués pour suppression.  
  
 *DatabaseName !* Spécifie le nom d’une base de données qui contient la table si la base de données qui le contient n’est pas la base de données spécifiée avec la source de données. Vous devez inclure le nom d’une base de données qui contient la table si la base de données n’est pas la base de données spécifiée avec la source de données. Inclure le séparateur de point d’exclamation ( !) après le nom de la base de données et avant le nom de table.  
  
 OÙ *FilterCondition1*[AND &#124; ou *FilterCondition2*...]  
 Spécifie que Visual FoxPro marquer uniquement certains enregistrements marqués en suppression.  
  
 *FilterCondition* spécifie les critères pour que les enregistrements marqués pour suppression. Vous pouvez inclure autant de conditions de filtre que vous le souhaitez, qui les connectent avec AND ou opérateur OR. Vous pouvez également utiliser l’opérateur NOT pour inverser la valeur d’une expression logique, ou vous pouvez utiliser **vide**() pour rechercher un champ vide.  
  
## <a name="remarks"></a>Notes  
 Si SET DELETED est définie sur ON, les enregistrements marqués pour suppression sont ignorées par toutes les commandes qui incluent une étendue.  
  
 DELETE - utilise SQL verrouillage des enregistrements lors du marquage de plusieurs enregistrements pour la suppression de tables ouvert pour l’accès partagé. Cela réduit la contention enregistrement dans les situations multi-utilisateur, mais peut réduire les performances. Pour optimiser les performances, ouvrez la table pour une utilisation exclusive.  
  
## <a name="driver-remarks"></a>Section Notes de pilote  
 Lorsque votre application envoie l’instruction SQL ODBC suppression à la source de données, le pilote ODBC Visual FoxPro convertit la commande dans la commande de suppression de Visual FoxPro sans traduction.  
  
## <a name="see-also"></a>Voir aussi  
 [SET DELETED, commande](../../odbc/microsoft/set-deleted-command.md)
