---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f713f9a0c96aaf3798cf160e648404470e3a4363
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064499"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Cette rubrique traite de l’utilisation de la fonction **SQLEndTran** dans la bibliothèque de curseurs. Pour obtenir des informations générales sur **SQLEndTran**, consultez [fonction SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
 La bibliothèque de curseurs ne prend pas en charge les transactions et transmet directement les appels à **SQLEndTran** au pilote. Toutefois, la bibliothèque de curseurs prend en charge les comportements de validation et de restauration de curseur tels qu’ils sont retournés par la source de données avec les types d’informations SQL_CURSOR_ROLLBACK_BEHAVIOR et SQL_CURSOR_COMMIT_BEHAVIOR :  
  
-   Pour les sources de données qui conservent des curseurs sur des transactions, les modifications qui sont restaurées dans la source de données ne sont pas restaurées dans le cache de la bibliothèque de curseurs. Pour que le cache corresponde aux données de la source de données, l’application doit fermer et rouvrir le curseur.  
  
-   Pour les sources de données qui ferment des curseurs au niveau des limites de transaction, la bibliothèque de curseurs ferme les curseurs et supprime les caches pour toutes les instructions sur la connexion.  
  
-   Pour les sources de données qui suppriment des instructions préparées au niveau des limites des transactions, l’application doit repréparer toutes les instructions préparées sur la connexion avant de les réexécuter.
