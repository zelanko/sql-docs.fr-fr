---
title: SQLEndTran (Cursor Library) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c2277a67cd5410ea3c2a5d5b03b16d4533ed6ee1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304769"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLEndTran** dans la bibliothèque de curseurs. Pour plus d’informations sur **SQLEndTran**, voir [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
 La bibliothèque de curseurs ne prend pas en charge les transactions et transmet les appels au **SQLEndTran** directement au conducteur. Cependant, la bibliothèque de curseur prend en charge les comportements de validation et de restauration du curseur tels que retournés par la source de données avec les types d’information SQL_CURSOR_ROLLBACK_BEHAVIOR et SQL_CURSOR_COMMIT_BEHAVIOR :  
  
-   Pour les sources de données qui préservent les curseurs dans toutes les transactions, les modifications qui sont annulées dans la source de données ne sont pas retournées dans le cache de la bibliothèque de curseurs. Pour faire correspondre le cache des données dans la source de données, l’application doit fermer et rouvrir le curseur.  
  
-   Pour les sources de données qui ferment les curseurs aux limites des transactions, la bibliothèque de curseurs ferme les curseurs et supprime les caches pour toutes les instructions sur la connexion.  
  
-   Pour les sources de données qui suppriment les relevés préparés aux limites des transactions, l’application doit reporéser toutes les déclarations préparées sur la connexion avant de les réexaminer.
