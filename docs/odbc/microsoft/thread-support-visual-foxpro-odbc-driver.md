---
title: Support de fil (Visual FoxPro ODBC Driver) Microsoft Docs
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
ms.openlocfilehash: 2aa19eb233525b5a65ef67fe9903814fc1163177
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303080"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Prise en charge des threads (pilote ODBC Visual FoxPro)
Le visual FoxPro ODBC Driver est sans fil. L’accès aux poignées de l’environnement *(poule),* aux poignées de connexion *(hdbc),* et aux poignées de déclaration *(hstmt*) est enveloppé dans des sémaphores appropriés pour empêcher d’autres processus d’accéder et potentiellement de modifier les structures de données internes du conducteur.  
  
 Dans une application multithreaded, vous pouvez annuler une fonction qui fonctionne de façon synchrone sur un *hstmt* en appelant [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) sur un thread séparé.  
  
 Le pilote utilise un thread séparé pour obtenir des données lorsque vous utilisez l’aller chercher progressif. Pour utiliser l’utilisation progressive de la recherche pour une source de données, sélectionnez les **données Fetch dans** la case à cocher de fond sur la boîte de dialogue [ODBC Visual FoxPro Setup](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) ou utilisez le mot clé d’attribut BackgroundFetch dans votre chaîne de connexion. Évitez d’utiliser l’arrière-plan aller chercher lorsque vous appelez le pilote à partir d’applications à plusieurs lues. Pour plus d’informations sur les mots clés d’attribut de chaîne de connexion, voir [Using Connection Strings](../../odbc/microsoft/using-connection-strings.md).  
  
 Pour plus d’informations sur les fils et **SQLCancel**, voir [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) dans la *référence du programmeur ODBC*.
