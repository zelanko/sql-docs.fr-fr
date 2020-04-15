---
title: Poignées d’environnement Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b504995e99dfad032598485e370b4d5a6681ae81
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300439"
---
# <a name="environment-handles"></a>Handles d’environnement
Un *environnement* est un contexte mondial dans lequel accéder aux données; associés à un environnement est toute information de nature mondiale, comme :  
  
-   L’état de l’environnement  
  
-   Les diagnostics actuels au niveau de l’environnement  
  
-   Les poignées de connexions actuellement allouées à l’environnement  
  
-   Les paramètres actuels de chaque attribut d’environnement  
  
 Dans un code qui implémente ODBC (le Driver Manager ou un pilote), une poignée d’environnement identifie une structure pour contenir ces informations.  
  
 Les poignées d’environnement ne sont pas fréquemment utilisées dans les applications ODBC. Ils sont toujours utilisés dans les appels à **SQLDataSources** et **SQLDrivers** et parfois utilisés dans les appels à **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**, et **SQLGetDiagRec**.  
  
 Chaque pièce de code qui implémente ODBC (le Driver Manager ou un pilote) contient une ou plusieurs poignées d’environnement. Par exemple, le gestionnaire de conducteur maintient une poignée d’environnement distincte pour chaque application qui y est connectée. Les poignées d’environnement sont attribuées avec **SQLAllocHandle** et libérées avec **SQLFreeHandle**.
