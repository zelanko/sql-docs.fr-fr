---
title: Déconnexion d’une données Source ou le pilote | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- disconnecting from driver [ODBC]
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
- connecting to data source [ODBC], disconnecting
- connecting to driver [ODBC], disconnecting
- ODBC drivers [ODBC], disconnecting
ms.assetid: 83dbf0bf-b400-41fb-8537-9b016050dc3c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2189c0fcc65fd4192e94da140e2d55ac86826137
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935998"
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Déconnexion d’une source de données ou d’un pilote
Lorsqu’une application a terminé d’utiliser une source de données, il appelle **SQLDisconnect**. **SQLDisconnect** libère toutes les instructions qui sont allouées sur la connexion et déconnecte le pilote de la source de données. Elle retourne une erreur si une transaction est en cours.  
  
 Après la déconnexion, l’application peut appeler **SQLFreeHandle** pour libérer la connexion. Après la libération de la connexion, il est une erreur de programmation d’application à utiliser le handle de la connexion dans un appel à une fonction ODBC ; Cette approche présente des conséquences non définis mais probablement irrécupérables. Lorsque **SQLFreeHandle** est appelée, les versions de pilote la structure utilisée pour stocker des informations sur la connexion.  
  
 L’application peut également réutiliser la connexion, soit pour vous connecter à une autre source de données ou de vous reconnecter à la même source de données. La décision de rester connectés, par opposition à la déconnexion et reconnexion plus tard, requiert que le rédacteur d’application considère les coûts relatifs de chaque option ; connexion à une source de données et de rester connectés peuvent être relativement coûteux selon le moyen de connexion. Pour effectuer un meilleur compromis, l’application doit également faire des hypothèses concernant la probabilité et le minutage des autres opérations sur la même source de données.
