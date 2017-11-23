---
title: Commande NULL SET | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ddc4b8a31a50c2f8ac0da02ffeaf2701a8a3e80
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="set-null-command"></a>Commande NULL SET
Détermine comment les valeurs null sont prises en charge par le SQL ALTER TABLE - SQL, CREATE TABLE - et INSERT - commandes SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 (Par défaut pour le pilote, la valeur par défaut pour Visual FoxPro est désactivé.) Spécifie que toutes les colonnes dans une table créée avec ALTER TABLE et CREATE TABLE autorise les valeurs null. Vous pouvez substituer la prise en charge de la valeur null pour les colonnes de la table en incluant la clause NOT NULL dans les définitions de colonnes.  
  
 Spécifie également que INSERT - SQL insère des valeurs null dans des colonnes non inclus dans l’instruction INSERT - clause SQL VALUE. INSERT - SQL insère des valeurs null uniquement dans des colonnes acceptant les valeurs null.  
  
 OFF  
 Spécifie que toutes les colonnes dans une table créée avec ALTER TABLE et CREATE TABLE ne permettent pas de valeurs null. Vous pouvez désigner la prise en charge de la valeur null pour les colonnes dans l’instruction ALTER TABLE et CREATE TABLE en incluant la clause de valeur NULL dans les définitions de colonnes.  
  
 Spécifie également que INSERT - SQL insère les valeurs vides dans des colonnes non inclus dans l’instruction INSERT - clause SQL VALUE.  
  
## <a name="remarks"></a>Notes  
 SET NULL affecte uniquement la nul est pris en charge par insertion - SQL ALTER TABLE et CREATE TABLE. Autres commandes ne sont pas affectées par la valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE - commande SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [CRÉER la TABLE - commande SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT, commande SQL](../../odbc/microsoft/insert-sql-command.md)
