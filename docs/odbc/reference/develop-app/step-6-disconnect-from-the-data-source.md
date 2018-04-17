---
title: 'Étape 6 : Vous déconnecter de la Source de données | Documents Microsoft'
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
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5271ba2554e726cc3855cb933f10882afad76fa0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="step-6-disconnect-from-the-data-source"></a>Étape 6 : Vous déconnecter de la Source de données
L’étape finale est pour vous déconnecter de la source de données, comme indiqué dans l’illustration suivante. Tout d’abord, l’application libère les handles d’instructions en appelant **SQLFreeHandle**. Pour plus d’informations, consultez [la libération d’un Handle d’instruction](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Affiche la déconnexion d’une source de données](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Ensuite, l’application se déconnecte de la source de données avec **SQLDisconnect** et libère le handle de connexion avec **SQLFreeHandle**. Pour plus d’informations, consultez [déconnexion d’une Source de données ou le pilote](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Enfin, l’application libère le handle d’environnement avec **SQLFreeHandle** et décharge le Gestionnaire de pilotes. Pour plus d’informations, consultez [allouer le Handle d’environnement](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
