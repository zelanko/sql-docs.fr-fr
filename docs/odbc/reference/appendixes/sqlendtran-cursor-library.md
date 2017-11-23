---
title: "SQLEndTran (bibliothèque de curseurs) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b7ca0f1299933293990fc2c977a4a6602f9d4400
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLEndTran** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLEndTran**, consultez [fonction SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
 Ne prend pas en charge les transactions de la bibliothèque de curseurs et passe les appels à **SQLEndTran** directement dans le pilote. Toutefois, la bibliothèque de curseurs ne prend pas en charge les comportements de curseur commit et rollback tel que retourné par la source de données avec les types d’informations SQL_CURSOR_ROLLBACK_BEHAVIOR et SQL_CURSOR_COMMIT_BEHAVIOR :  
  
-   Pour les sources de données qui conservent les curseurs entre les transactions, les modifications sont restaurées dans la source de données ne sont pas restaurées dans le cache de la bibliothèque de curseurs. Pour rendre le cache correspondent aux données dans la source de données, l’application doit fermer et rouvrir le curseur.  
  
-   Pour les sources de données qui ferment les curseurs des limites de transaction, la bibliothèque de curseurs ferme le curseur et supprime le met en cache pour toutes les instructions sur la connexion.  
  
-   Pour les sources de données supprimer les instructions préparées au niveau des limites de transaction, l’application doit reprepare toutes les instructions préparées sur la connexion avant de les réexécuter.
