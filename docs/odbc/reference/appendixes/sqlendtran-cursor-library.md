---
description: SQLEndTran (bibliothèque de curseurs)
title: SQLEndTran (bibliothèque de curseurs) | Microsoft Docs
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
ms.openlocfilehash: 25584f19a885580be24b2681ccd639de285fb4b2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466031"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Cette rubrique traite de l’utilisation de la fonction **SQLEndTran** dans la bibliothèque de curseurs. Pour obtenir des informations générales sur **SQLEndTran**, consultez [fonction SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
 La bibliothèque de curseurs ne prend pas en charge les transactions et transmet directement les appels à **SQLEndTran** au pilote. Toutefois, la bibliothèque de curseurs prend en charge les comportements de validation et de restauration de curseur tels qu’ils sont retournés par la source de données avec les types d’informations SQL_CURSOR_ROLLBACK_BEHAVIOR et SQL_CURSOR_COMMIT_BEHAVIOR :  
  
-   Pour les sources de données qui conservent des curseurs sur des transactions, les modifications qui sont restaurées dans la source de données ne sont pas restaurées dans le cache de la bibliothèque de curseurs. Pour que le cache corresponde aux données de la source de données, l’application doit fermer et rouvrir le curseur.  
  
-   Pour les sources de données qui ferment des curseurs au niveau des limites de transaction, la bibliothèque de curseurs ferme les curseurs et supprime les caches pour toutes les instructions sur la connexion.  
  
-   Pour les sources de données qui suppriment des instructions préparées au niveau des limites des transactions, l’application doit repréparer toutes les instructions préparées sur la connexion avant de les réexécuter.
