---
title: Poignées de connexion Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: 12222653-f04d-46d6-bdee-61348f5d550f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d5b03e0733e35984350d2a218b885dc148ca8f8f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299019"
---
# <a name="connection-handles"></a>Handles de connexion
Une *connexion* se compose d’un conducteur et d’une source de données. Une poignée de connexion identifie chaque connexion. La poignée de connexion définit non seulement quel pilote utiliser, mais quelle source de données utiliser avec ce conducteur. Dans un segment de code qui implémente ODBC (le gestionnaire de conducteur ou un pilote), la poignée de connexion identifie une structure qui contient des informations de connexion, telles que les suivantes :  
  
-   L’état de la connexion  
  
-   Les diagnostics actuels au niveau de connexion  
  
-   Les poignées d’instructions et de descripteurs actuellement alloués à la connexion  
  
-   Les paramètres actuels de chaque attribut de connexion  
  
 ODBC n’empêche pas plusieurs connexions simultanées, si le conducteur les prend en charge. Par conséquent, dans un environnement particulier ODBC, les poignées de connexion multiples peuvent indiquer une variété de pilotes et de sources de données, au même conducteur et à une variété de sources de données, ou même à plusieurs connexions au même conducteur et à la même source de données. Certains conducteurs limitent le nombre de connexions actives qu’ils prennent en charge; l’option SQL_MAX_DRIVER_CONNECTIONS dans **SQLGetInfo** précise le nombre de connexions actives qu’un conducteur prend en charge.  
  
 Les poignées de connexion sont principalement utilisées lors de la connexion à la source de données (**SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**), déconnectant de la source de données (**SQLDisconnect**), obtenir des informations sur le conducteur et la source de données (**SQLGetInfo**), récupérer des diagnostics (**SQLGetDiagField** et **SQLGetDiagRec**), et effectuer des transactions (**SQLEndTran**). Ils sont également utilisés lors du réglage et de l’obtention d’attributs de connexion (**SQLSetConnectAttr** et **SQLGetConnectAttr**) et lors de l’obtention du format natif d’une déclaration SQLL (**SQLNativeSql**).  
  
 Les poignées de connexion sont attribuées à **SQLAllocHandle** et libérées avec **SQLFreeHandle**.
