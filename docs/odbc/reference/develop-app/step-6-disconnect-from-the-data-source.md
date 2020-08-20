---
description: 'Étape 6 : Se déconnecter de la source de données'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 06b3b50653578388ca3d4e20b598f63879f38e88
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461341"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Étape 6 : Se déconnecter de la source de données
La dernière étape consiste à se déconnecter de la source de données, comme indiqué dans l’illustration suivante. Tout d’abord, l’application libère tous les descripteurs d’instruction en appelant **SQLFreeHandle**. Pour plus d’informations, consultez [libération d’un descripteur d’instruction](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Présente la déconnexion d'une source de données](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Ensuite, l’application se déconnecte de la source de données avec **SQLDisconnect** et libère le handle de connexion avec **SQLFreeHandle**. Pour plus d’informations, consultez [déconnexion d’une source de données ou d’un pilote](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Enfin, l’application libère le handle d’environnement avec **SQLFreeHandle** et décharge le gestionnaire de pilotes. Pour plus d’informations, consultez [allocation du handle d’environnement](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
