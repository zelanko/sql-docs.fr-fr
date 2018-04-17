---
title: SQLTransact (le pilote ODBC Visual FoxPro) | Documents Microsoft
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
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4f787e04610187011b12c25ce738432066120365
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau principal  
  
 Demande une opération de validation ou de restauration pour toutes les opérations actives sur tous les descripteurs d’instruction (*hstmt*s) associés à une connexion ou pour toutes les connexions associées au handle d’environnement, *henv*. **SQLTransact** fonctionne uniquement pour les sources de données qui sont [bases de données](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Si une validation échoue en mode manuel, la transaction reste active ; Vous pouvez choisir de restaurer la transaction ou recommencez l’opération de validation. Si une opération de validation échoue en mode de transaction automatique, la transaction est restaurée automatiquement ; la transaction ne peut pas être inactive.  
  
 Pour plus d’informations, consultez [SQLTransact](../../odbc/reference/syntax/sqltransact-function.md) dans les *de référence du programmeur ODBC*.
