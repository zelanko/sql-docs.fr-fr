---
title: "SQLSetScrollOptions (pilotes d’ordinateur de bureau) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd83d7ce68d0a7bc1045aee76c28b9b5c39c9faf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (pilotes bureau de base de données)
Les curseurs avant et statiques sont prises en charge pour la valeur SQL_CONCUR_READ_ONLY.  
  
 Uniquement les curseurs pilotés par jeu de clés sont pris en charge pour un *fConcurrency* argument de SQL_CONCUR_LOCK.  
  
 Un *fConcurrency* argument de SQL_CONCUR_ROWVER n’est pas pris en charge.  
  
 Les curseurs dynamiques et les curseurs mixtes ne sont pas pris en charge.
