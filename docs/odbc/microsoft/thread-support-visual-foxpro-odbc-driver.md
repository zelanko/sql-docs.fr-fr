---
title: Prise en charge (pilote ODBC de Visual FoxPro) thread | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77187802bb57a832263ec2070564754e87f21345
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62632922"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Prise en charge des threads (pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro est thread-safe. Accès aux handles d’environnement (*poule*), les handles de connexion (*pas*) et les descripteurs d’instruction (*hstmt*) est encapsulée dans des sémaphores appropriées pour empêcher les autres processus à partir de l’accès à et potentiellement modifier les structures de données internes du pilote.  
  
 Dans une application multithread, vous pouvez annuler une fonction qui s’exécute de façon synchrone sur un *hstmt* en appelant [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) sur un thread distinct.  
  
 Le pilote utilise un thread distinct pour extraire des données lorsque vous utilisez l’extraction progressif. Pour utiliser l’extraction progressif pour une source de données, sélectionnez le **extraire les données en arrière-plan** case à cocher sur la [boîte de dialogue d’installation de ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) ou utiliser le mot clé d’attribut BackgroundFetch dans votre connexion chaîne. Évitez d’utiliser l’extraction en arrière-plan lorsque vous appelez le pilote à partir d’applications multithreads. Pour plus d’informations sur les mots clés attribut de chaîne de connexion, consultez [à l’aide de chaînes de connexion](../../odbc/microsoft/using-connection-strings.md).  
  
 Pour plus d’informations sur les threads et **SQLCancel**, consultez [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) dans le *de référence du programmeur ODBC*.
