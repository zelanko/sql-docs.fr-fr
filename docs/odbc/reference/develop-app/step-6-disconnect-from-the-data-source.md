---
title: 'Étape 6 : se déconnecter de la source de données | Microsoft Docs'
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114120"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Étape 6 : Se déconnecter de la source de données
La dernière étape consiste à se déconnecter de la source de données, comme indiqué dans l’illustration suivante. Tout d’abord, l’application libère tous les descripteurs d’instruction en appelant **SQLFreeHandle**. Pour plus d’informations, consultez [libération d’un descripteur d’instruction](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Présente la déconnexion d'une source de données](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Ensuite, l’application se déconnecte de la source de données avec **SQLDisconnect** et libère le handle de connexion avec **SQLFreeHandle**. Pour plus d’informations, consultez [déconnexion d’une source de données ou d’un pilote](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Enfin, l’application libère le handle d’environnement avec **SQLFreeHandle** et décharge le gestionnaire de pilotes. Pour plus d’informations, consultez [allocation du handle d’environnement](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
