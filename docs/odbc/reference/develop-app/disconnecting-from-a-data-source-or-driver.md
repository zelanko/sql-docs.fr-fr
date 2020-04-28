---
title: Déconnexion d’une source de données ou d’un pilote | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 154a571bce3a337d539216ce89c32420ab981bd8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300459"
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Déconnexion d’une source de données ou d’un pilote
Lorsqu’une application a fini d’utiliser une source de données, elle appelle **SQLDisconnect**. **SQLDisconnect** libère toutes les instructions qui sont allouées sur la connexion et déconnecte le pilote de la source de données. Elle retourne une erreur si une transaction est en cours.  
  
 Après la déconnexion, l’application peut appeler **SQLFreeHandle** pour libérer la connexion. Une fois la connexion libérée, il s’agit d’une erreur de programmation d’application pour utiliser le handle de la connexion dans un appel à une fonction ODBC. Cela a des conséquences non définies mais probablement irrécupérables. Quand **SQLFreeHandle** est appelé, le pilote libère la structure utilisée pour stocker des informations sur la connexion.  
  
 L’application peut également réutiliser la connexion, soit pour se connecter à une autre source de données, soit pour se reconnecter à la même source de données. La décision de rester connectée, au lieu de se déconnecter et de se reconnecter ultérieurement, exige que le rédacteur d’application considère les coûts relatifs de chaque option ; la connexion à une source de données et la connexion restante peuvent être relativement coûteuses en fonction du support de connexion. Pour faire un compromis correct, l’application doit également faire des hypothèses sur la probabilité et le minutage des opérations supplémentaires sur la même source de données.
