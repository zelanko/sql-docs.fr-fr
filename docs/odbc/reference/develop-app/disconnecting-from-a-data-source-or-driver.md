---
title: Déconnecter les données Source ou le pilote | Documents Microsoft
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
- disconnecting from driver [ODBC]
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
- connecting to data source [ODBC], disconnecting
- connecting to driver [ODBC], disconnecting
- ODBC drivers [ODBC], disconnecting
ms.assetid: 83dbf0bf-b400-41fb-8537-9b016050dc3c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a1e0e89632c1c39df415c8db3a9f29c9c724c2d9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Déconnecter les données Source ou pilote
Lorsqu’une application a fini d’utiliser une source de données, il appelle **SQLDisconnect**. **SQLDisconnect** libère toutes les instructions qui sont allouées sur la connexion et déconnecte le pilote de la source de données. Il renvoie une erreur si une transaction est en cours.  
  
 Après la déconnexion, l’application peut appeler **SQLFreeHandle** pour libérer la connexion. Après la libération de la connexion, il s’agit d’une erreur de programmation d’application à utiliser le handle de la connexion dans un appel à une fonction ODBC ; Cette opération donc des conséquences non défini mais probablement irrécupérable. Lorsque **SQLFreeHandle** est appelée, les versions de pilote la structure utilisée pour stocker des informations sur la connexion.  
  
 L’application également peut réutiliser la connexion, pour se connecter à une autre source de données ou de se reconnecter à la même source de données. La décision de rester connecté, par opposition à déconnecter et vous reconnecter plus tard, requiert que le rédacteur d’application considère les coûts relatifs de chaque option ; connexion à une source de données et de connexion peuvent être relativement coûteux selon le support de connexion. Pour effectuer un compromis approprié, l’application doit également faire d’hypothèses sur la probabilité et le minutage des autres opérations sur la même source de données.
