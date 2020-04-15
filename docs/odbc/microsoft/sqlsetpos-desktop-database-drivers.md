---
title: SQLSetPos (Desktop Database Drivers) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Desktop Database Drivers
ms.assetid: 8ef027ec-8512-48fe-8fe2-2ff7cd81e331
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e151e3abc4032ea3180e46360c501d9fbea9ae30
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301460"
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (pilotes pour les bases de données de poste de travail)
La sémantique de modèle en vrac pour les appels **SQLSetPos** avec *l’argument irow* égal à 0 sont pris en charge.  
  
 SQL_LOCK_NO_CHANGE est pris en charge pour *fLock*. SQL_LOCK_EXCLUSIVE et SQL_LOCK_UNLOCK ne sont pas pris en charge.  
  
 **SQLSetPos** prend en charge les jointures updatable. (Pour plus d’informations, consultez le *Guide du programmeur de moteurs microsoft Jet Database Engine*.)
