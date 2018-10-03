---
title: INSERT, commande SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa2211ddef09e127b66430968792007d29dd5eb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840097"
---
# <a name="insert---sql-command"></a>INSERT, commande SQL
Ajoute un enregistrement à la fin d’une table qui contient les valeurs de champ spécifié.  
  
 Le pilote ODBC Visual FoxPro prend en charge la syntaxe du langage Visual FoxPro native pour cette commande. Pour plus d’informations spécifiques au pilote, consultez la section Notes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Arguments  
 INSERT INTO *dbf_name*  
 Spécifie le nom de la table à laquelle le nouvel enregistrement est ajouté. *dbf_name* peut inclure un chemin d’accès et peut être une expression de nom.  
  
 Si la table que vous spécifiez n’est pas ouverte, il est ouvert en mode exclusif dans une nouvelle zone de travail et le nouvel enregistrement est ajouté à la table. La nouvelle zone de travail n’est pas sélectionnée ; la zone de travail actuel est sélectionnée.  
  
 Si la table que vous spécifiez est ouverte, INSERT ajoute le nouvel enregistrement à la table. Si la table est ouverte dans une zone de travail autres que la zone de travail actuel, il n’est pas sélectionné après l’ajout de l’enregistrement ; la zone de travail actuel est sélectionnée.  
  
 [( *fname1*[, *fname2*[,...]])]  
 Spécifie, dans le nouvel enregistrement, les noms des champs dans lesquels les valeurs sont insérées.  
  
 VALEURS ( *eExpression1*[, *eExpression2*[,...]])  
 Spécifie les valeurs de champ insérés dans le nouvel enregistrement. Si vous omettez les noms de champ, vous devez spécifier les valeurs de champ dans l’ordre défini par la structure de table.  
  
## <a name="remarks"></a>Notes  
 Le nouvel enregistrement contient les données répertoriées dans la clause VALUES.  
  
## <a name="driver-remarks"></a>Notes de pilote  
 Lorsque votre application envoie l’instruction ODBC SQL INSERT à la source de données, le pilote ODBC Visual FoxPro convertit la commande dans la commande FoxProINSERT Visual sans traduction.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TABLE, commande SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT, commande SQL](../../odbc/microsoft/select-sql-command.md)
