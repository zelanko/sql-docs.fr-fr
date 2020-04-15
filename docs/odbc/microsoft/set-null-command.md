---
title: Set NULL Commande ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c83c9ef9f8a0ce143308b73d8df09b05fb2cdea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300809"
---
# <a name="set-null-command"></a>SET NULL, commande
Détermine comment les valeurs nulles sont soutenues par le TABLE ALTER - SQL, CREATE TABLE - SQL, et INSERT - SQL commandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ACTIVÉ  
 (Par défaut pour le pilote; la valeur par défaut pour Visual FoxPro est OFF.) Précise que toutes les colonnes d’un tableau créé avec ALTER TABLE et CREATE TABLE permettent des valeurs nulles. Vous pouvez remplacer la prise en charge de valeur nulle pour les colonnes dans le tableau en incluant la clause NOT NULL dans les définitions des colonnes.  
  
 Précise également que INSERT - SQL insérera des valeurs nulles dans les colonnes qui ne sont pas incluses dans la clause INSERT - SQL VALUE. INSERT - SQL insérera des valeurs nulles uniquement dans des colonnes qui permettent des valeurs nulles.  
  
 OFF  
 Précise que toutes les colonnes d’un tableau créé avec ALTER TABLE et CREATE TABLE n’autorisent pas les valeurs nulles. Vous pouvez désigner le support de valeur nulle pour les colonnes dans ALTER TABLE et CREATE TABLE en incluant la clause NULL dans les définitions des colonnes.  
  
 Précise également que INSERT - SQL insérera des valeurs vierges dans toutes les colonnes qui ne sont pas incluses dans la clause INSERT - SQL VALUE.  
  
## <a name="remarks"></a>Notes  
 SET NULL n’affecte que la façon dont les valeurs nulles sont soutenues par ALTER TABLE, CREATE TABLE et INSERT - SQL. D’autres commandes ne sont pas affectées par SET NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE - Commandement SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [TABLE CREATE - Commandement SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT, commande SQL](../../odbc/microsoft/insert-sql-command.md)
