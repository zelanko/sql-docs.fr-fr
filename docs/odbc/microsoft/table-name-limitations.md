---
title: Limitations des noms de table | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 152a0aa1e8d92424b2f60c49f44888de7d3e528c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939777"
---
# <a name="table-name-limitations"></a>Limitations des noms de table
Noms de table peuvent contenir des caractères valides (par exemple, des espaces). Si les noms de tables contiennent des caractères à l’exception des lettres, des chiffres et des traits de soulignement, le nom doit être délimité en l’entourant de guillemets précédent (').  
  
 Lorsque le pilote Microsoft Excel est utilisé, et un nom de table n’est pas qualifié par une référence de base de données, la base de données par défaut est implicite. Si un nom dans Microsoft Excel inclut le « ! » caractères, il sera automatiquement traduit vers le caractère « $» à la place.  
  
 Le nom de table de Microsoft Excel qui fait référence à \<filename > est pris en charge pour Microsoft Excel version 3.0 et 4.0 fichiers. Le nom de table de Microsoft Excel qui fait référence à \<classeur-name > est prise en charge pour les fichiers Microsoft Excel 5.0, 7.0 ou 97.  
  
 Lorsque le pilote dBASE est utilisé, les caractères avec une valeur ASCII supérieure à 127 sont convertis en traits de soulignement.  
  
 Lorsque le pilote Microsoft Access est utilisé, le nom de table est limité à 64 caractères.  
  
 Lorsque le pilote de Microsoft Excel 3.0 ou 4.0, Paradox, ou du texte dBASE, est utilisé, les mots clés MS-DOS spéciaux CON, AUX, LPT1, LPT2 et ne doivent pas utilisés comme noms de tables.
