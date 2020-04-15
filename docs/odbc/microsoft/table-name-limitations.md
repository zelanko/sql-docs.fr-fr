---
title: Limitations du nom de table (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 738c563961eae56471f0238d9726a1ebb0bdc76e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289215"
---
# <a name="table-name-limitations"></a>Limitations des noms de table
Les noms de table peuvent contenir tous les caractères valides (par exemple, les espaces). Si les noms de table contiennent des caractères, sauf des lettres, des chiffres et des points de souligne, le nom doit être délimité en l’enfermant dans des citations de dos (').  
  
 Lorsque le pilote Microsoft Excel est utilisé et qu’un nom de table n’est pas qualifié par une référence de base de données, la base de données par défaut est implicite. Si un nom dans Microsoft Excel inclut le personnage "!", il sera automatiquement traduit au personnage "$" à la place.  
  
 Le nom de table \<Microsoft Excel qui fait référence au nom de fichier> est pris en charge pour les fichiers Microsoft Excel 3.0 et 4.0. Le nom de table \<Microsoft Excel qui fait référence à la> de nom de manuel est pris en charge pour les fichiers Microsoft Excel 5.0, 7.0 ou 97.  
  
 Lorsque le pilote dBASE est utilisé, les caractères d’une valeur ASCII supérieure à 127 sont convertis en souligne.  
  
 Lorsque le pilote Microsoft Access est utilisé, le nom de table est limité à 64 caractères.  
  
 Lorsque le dBASE, Microsoft Excel 3.0 ou 4.0, Paradox, ou le pilote de texte est utilisé, les mots clés SPÉCIAux MS-DOS CON, AUX, LPT1 et LPT2 ne doivent pas être utilisés comme noms de table.
