---
description: Prise en charge des threads (pilote ODBC Visual FoxPro)
title: Prise en charge des threads (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 013ccd1f5d202794ba6b7a44c10339dd14c08d17
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449071"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Prise en charge des threads (pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro est thread-safe. L’accès aux descripteurs de l’environnement (*poules*), les handles de connexion (*hdbc*) et les descripteurs d’instructions (*HSTMT*) est encapsulé dans les sémaphores appropriés pour empêcher d’autres processus d’accéder aux structures de données internes du pilote et éventuellement de les modifier.  
  
 Dans une application multithread, vous pouvez annuler une fonction qui s’exécute de façon synchrone sur un *HSTMT* en appelant [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) sur un thread distinct.  
  
 Le pilote utilise un thread distinct pour extraire des données lorsque vous utilisez la récupération progressive. Pour utiliser l’extraction progressive pour une source de données, activez la case à cocher **extraire les données en arrière-plan** dans la boîte de [dialogue installation de ODBC pour Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) ou utilisez le mot clé d’attribut BackgroundFetch dans votre chaîne de connexion. Évitez d’utiliser la récupération en arrière-plan lorsque vous appelez le pilote à partir d’applications multithread. Pour plus d’informations sur les mots clés d’attribut de chaîne de connexion, consultez [utilisation de chaînes de connexion](../../odbc/microsoft/using-connection-strings.md).  
  
 Pour plus d’informations sur les threads et les **SQLCancel**, consultez [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) dans le *Guide de référence du programmeur ODBC*.
