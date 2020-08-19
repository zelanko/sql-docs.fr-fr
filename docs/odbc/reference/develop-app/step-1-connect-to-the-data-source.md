---
description: 'Étape 1 : Se connecter à la source de données'
title: 'Étape 1 : se connecter à la source de données | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ac15eed6c84745dca6406ad8186f14c65798939
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482962"
---
# <a name="step-1-connect-to-the-data-source"></a>Étape 1 : Se connecter à la source de données
La première étape d’une application consiste à se connecter à la source de données. Cette phase, y compris les fonctions requises, est présentée dans l’illustration suivante.  
  
 ![Connexion à la source de données dans une application ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 La première étape de la connexion à la source de données consiste à charger le gestionnaire de pilotes et à allouer le descripteur d’environnement avec **SQLAllocHandle**. Pour plus d’informations, consultez [allocation du handle d’environnement](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 L’application inscrit ensuite la version de ODBC à laquelle elle se conforme en appelant **SQLSetEnvAttr** avec l’attribut d’environnement SQL_ATTR_APP_ODBC_VER. Pour plus d’informations, consultez [déclaration de la version ODBC de l’application](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) et [compatibilité descendante et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Ensuite, l’application alloue un descripteur de connexion avec **SQLAllocHandle** et se connecte à la source de données avec **SQLConnect**, **SQLDriverConnect**ou **SQLBrowseConnect**. Pour plus d’informations, consultez [allocation d’un handle de connexion](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) et [établissement d’une connexion](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 L’application définit ensuite tous les attributs de connexion, par exemple s’il faut valider manuellement les transactions. Pour plus d’informations, consultez [attributs de connexion](../../../odbc/reference/develop-app/connection-attributes.md).
