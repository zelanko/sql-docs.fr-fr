---
title: SET NULL, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b6f0e23abd31661210282967fa35080376eaaaf3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765627"
---
# <a name="set-null-command"></a>SET NULL, commande
Détermine comment les valeurs null sont prises en charge par le SQL ALTER TABLE (SQL, CREATE TABLE) et INSERT - commandes SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 (Par défaut pour le pilote ; la valeur par défaut pour Visual FoxPro est désactivée (OFF).) Spécifie que toutes les colonnes dans une table créée avec ALTER TABLE et CREATE TABLE autorise les valeurs null. Vous pouvez remplacer la prise en charge de la valeur null pour les colonnes dans le tableau en incluant la clause NOT NULL dans les définitions de la colonne.  
  
 Spécifie également que INSERT - SQL insère des valeurs null dans toutes les colonnes non inclus dans l’instruction INSERT - clause SQL VALUE. INSERT - SQL insère des valeurs null uniquement dans les colonnes qui acceptent les valeurs null.  
  
 OFF  
 Spécifie que toutes les colonnes dans une table créée avec ALTER TABLE et CREATE TABLE ne permettent pas de valeurs null. Vous pouvez désigner la prise en charge de la valeur null pour les colonnes dans l’instruction ALTER TABLE et CREATE TABLE en incluant la clause NULL dans les définitions de la colonne.  
  
 Spécifie également que INSERT - SQL insère les valeurs vides dans toutes les colonnes non inclus dans l’instruction INSERT - clause SQL VALUE.  
  
## <a name="remarks"></a>Notes  
 SET NULL affecte uniquement comment nul est pris en charge par ALTER TABLE, CREATE TABLE et INSERT - SQL. Autres commandes ne sont pas affectées par la valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE, commande SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [CREATE TABLE, commande SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT, commande SQL](../../odbc/microsoft/insert-sql-command.md)
