---
title: 'Étape 6 : Déconnexion de la Source de données | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65cc2ae8d2c2248a733e6efa9537fd3b40bb8fd1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114120"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Étape 6 : Se déconnecter de la source de données
L’étape finale consiste à déconnecter à partir de la source de données, comme indiqué dans l’illustration suivante. Tout d’abord, l’application libère les descripteurs d’instruction en appelant **SQLFreeHandle**. Pour plus d’informations, consultez [libération d’un Handle d’instruction](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Présente la déconnexion d’une source de données](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Ensuite, l’application se déconnecte de la source de données avec **SQLDisconnect** et libère le handle de connexion avec **SQLFreeHandle**. Pour plus d’informations, consultez [déconnexion d’une Source de données ou le pilote](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Enfin, l’application libère le handle d’environnement avec **SQLFreeHandle** et décharge le Gestionnaire de pilotes. Pour plus d’informations, consultez [allouer le Handle d’environnement](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
