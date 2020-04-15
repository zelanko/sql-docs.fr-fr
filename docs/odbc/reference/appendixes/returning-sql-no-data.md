---
title: Retour SQL_NO_DATA Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e2c806edd5d5647e09c00975ad7207ee5c2c876
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305110"
---
# <a name="returning-sql_no_data"></a>Retour de SQL_NO_DATA
Lorsqu’une application ODBC *2.x* fonctionnant avec un conducteur ODBC *3.x* appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData**, et une mise à jour recherchée ou une déclaration de suppression a été exécutée mais n’a pas affecté les lignes à la source de données, le conducteur ODBC *3.x* devrait retourner SQL_SUCCESS. Lorsqu’une application ODBC *3.x* travaillant avec un conducteur ODBC *3.x* appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** avec le même résultat, le conducteur ODBC *3.x* devrait retourner SQL_NO_DATA.  
  
 Si une mise à jour recherchée ou supprime l’instruction dans un lot d’instructions n’affecte aucune ligne à la source de données, **SQLMoreResults** retourne SQL_SUCCESS. Il ne peut pas retourner SQL_NO_DATA, parce que cela signifierait qu’il n’y a plus de résultats, pas qu’il y ait un résultat d’une mise à jour recherchée / supprimer qui n’a affecté aucune ligne.
