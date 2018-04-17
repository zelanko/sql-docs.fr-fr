---
title: Appel SQLCloseCursor | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 805c06c225a457b26467189c4b33b4ee10db828e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="calling-sqlclosecursor"></a>Appel SQLCloseCursor
Étant donné que **SQLCloseCursor** est presque identique **SQLFreeStmt** avec SQL_CLOSE, le Gestionnaire de pilotes ne mappe pas cette fonction. Fonctions de remplacement sont mappées afin qu’existant ODBC 2*.x* applications peuvent facilement transférer dans ODBC 3. *x* à l’aide des nouvelles fonctions. Une telle opération plus facilement ces applications commencer à l’aide de la nouvelle ODBC 3. *x* fonctionnalité à l’intérieur d’un code conditionnel de façon modulaire. **SQLCloseCursor** ne représente pas de nouvelles fonctionnalités. Une application ne peut pas accéder les avantages en déplaçant vers **SQLCloseCursor** de **SQLFreeStmt** avec SQL_CLOSE.
