---
title: Combinaisons de type cursur et de concurrence (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6397b5d675546bf41102f037b68c0022bec74df
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280769"
---
# <a name="cursor-type-and-concurrency-combinations"></a>Combinaisons des types de curseurs et des accès concurrentiels
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Les types de curseurs contrôlent la fonctionnalité du curseur fourni à l’utilisateur. Les options de concordance contrôlent la facilité d’updatabilité et le comportement de verrouillage d’un ensemble de résultats.  
  
|Type de curseur|Concurrency (valeurs autorisées)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1]</sup> Voir [les limites de l’utilisation des curseurs keyset-Driven](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2]</sup> SQL_CONCUR_LOCK n’est pris en charge que lorsque l’option de connexion SQL_AUTOCOMMIT est réglée pour SQL_AUTOCOMMIT_OFF.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de connexion](../../odbc/microsoft/connect-options.md)
