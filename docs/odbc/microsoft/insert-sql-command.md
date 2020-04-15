---
title: INSERT - Commandement SQL Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ce00005fb1aa0ca9732fc5e9cfeacd6faf6ef9e1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300003"
---
# <a name="insert---sql-command"></a>INSERT, commande SQL
Annexe un enregistrement à la fin d’un tableau qui contient les valeurs de champ spécifiées.  
  
 Le Visual FoxPro ODBC Driver prend en charge la syntaxe en langue visuelle FoxPro native pour cette commande. Pour obtenir des renseignements spécifiques au conducteur, consultez les remarques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Arguments  
 INSERT DANS *dbf_name*  
 Précise le nom de la table à laquelle le nouvel enregistrement est joint. *dbf_name* peut inclure un chemin et peut être une expression de nom.  
  
 Si la table que vous spécifiez n’est pas ouverte, elle est ouverte exclusivement dans une nouvelle zone de travail et le nouvel enregistrement est joint à la table. La nouvelle zone de travail n’est pas sélectionnée; la zone de travail actuelle reste sélectionnée.  
  
 Si la table que vous spécifiez est ouverte, INSERT joint le nouvel enregistrement à la table. Si la table est ouverte dans une zone de travail autre que la zone de travail actuelle, elle n’est pas sélectionnée après l’appendice; la zone de travail actuelle reste sélectionnée.  
  
 *[() fname1*[, *fname2*[,]]]  
 Spécifie dans le nouvel enregistrement les noms des champs dans lesquels les valeurs sont insérées.  
  
 VALUES ( *eExpression1*[, *eExpression2*[,]]  
 Spécifie les valeurs de champ insérées dans le nouveau record. Si vous ometez les noms de champ, vous devez spécifier les valeurs de champ dans l’ordre défini par la structure de la table.  
  
## <a name="remarks"></a>Notes  
 Le nouvel enregistrement contient les données énumérées dans la clause VALUES.  
  
## <a name="driver-remarks"></a>Remarques du conducteur  
 Lorsque votre application envoie la déclaration SQL ODBC INSERT à la source de données, le visual FoxPro ODBC Driver convertit la commande en commande Visual FoxProINSERT sans traduction.  
  
## <a name="see-also"></a>Voir aussi  
 [TABLE CREATE - Commandement SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT, commande SQL](../../odbc/microsoft/select-sql-command.md)
