---
title: DELETE - Commandement SQL Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE [ODBC]
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9757fd57d999815964266c035963de1129eaf5e8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303550"
---
# <a name="delete---sql-command"></a>DELETE, commande SQL
Marque les enregistrements de suppression.  
  
 Le Visual FoxPro ODBC Driver prend en charge la syntaxe en langue visuelle FoxPro native pour cette commande. Pour obtenir des renseignements spécifiques au conducteur, consultez les remarques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DELETE FROM [DatabaseName!]TableName  
   [WHERE FilterCondition1 [AND | OR FilterCondition2 ...]]  
```  
  
## <a name="arguments"></a>Arguments  
 DE [ *DatabaseName!*] *Nom de la table*  
 Spécifie le tableau dans lequel les enregistrements sont marqués pour la suppression.  
  
 *Databasename!* spécifie le nom d’une base de données qui contient la table si la base de données contenante n’est pas la base de données spécifiée avec la source de données. Vous devez inclure le nom d’une base de données qui contient la table si la base de données n’est pas la base de données spécifiée avec la source de données. Inclure le point d’exclamation (!) delimiter après le nom de la base de données et avant le nom de table.  
  
 Où *FilterCondition1*[ET &#124; OU *FilterCondition2*...]  
 Précise que Visual FoxPro ne marque que certains enregistrements pour la suppression.  
  
 *FilterCondition* spécifie les critères que les enregistrements doivent respecter pour être marqués pour la suppression. Vous pouvez inclure autant de conditions de filtre que vous le souhaitez, en les connectant avec l’ET ou l’opérateur OU. Vous pouvez également utiliser l’opérateur PAS pour inverser la valeur d’une expression logique, ou vous pouvez utiliser **EMPTY**( ) pour vérifier un champ vide.  
  
## <a name="remarks"></a>Notes  
 Si SET DELETED est réglé sur ON, les enregistrements marqués pour la suppression sont ignorés par toutes les commandes qui incluent une portée.  
  
 DELETE - SQL utilise le verrouillage des enregistrements lors du marquage de plusieurs enregistrements pour la suppression dans les tables ouvertes pour un accès partagé. Cela réduit la contention des records dans les situations multi-autres, mais peut diminuer les performances. Pour un maximum de performances, ouvrez la table pour une utilisation exclusive.  
  
## <a name="driver-remarks"></a>Remarques du conducteur  
 Lorsque votre application envoie la déclaration SQL D’ODBC SUPPRIMER à la source de données, le visual FoxPro ODBC Driver convertit la commande en commande Visual FoxPro DELETE sans traduction.  
  
## <a name="see-also"></a>Voir aussi  
 [SET DELETED, commande](../../odbc/microsoft/set-deleted-command.md)
