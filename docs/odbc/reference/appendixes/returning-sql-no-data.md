---
title: Retournant SQL_NO_DATA | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2613593d9c2e20d5dfa01c0a0b4f9886dbc8e889
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057129"
---
# <a name="returning-sqlnodata"></a>Retour de SQL_NO_DATA
Lorsqu’une application ODBC *2.x* workingwith application une application ODBC *3.x* pilote appelle **SQLExecDirect**, **SQLExecute**, ou  **SQLParamData**, et une mise à jour recherchée ou l’instruction delete a été exécutée mais n’a affecté aucune ligne à la source de données ODBC *3.x* pilote doit retourner SQL_SUCCESS. Lorsqu’une application ODBC *3.x* application fonctionne avec une application ODBC *3.x* pilote appelle **SQLExecDirect**, **SQLExecute**, ou  **SQLParamData** avec le même résultat, ODBC *3.x* pilote doit retourner SQL_NO_DATA.  
  
 Si une recherche de mettre à jour ou de supprimer l’instruction dans un lot d’instructions n’affecte pas toutes les lignes à la source de données **SQLMoreResults** retourne SQL_SUCCESS. Il ne peut pas retourner SQL_NO_DATA, car cela signifierait qu’il n’y a plus aucun résultat, pas qu’il est un résultat à partir d’une mise à jour/delete par recherche qui a n’affecté aucune ligne.
