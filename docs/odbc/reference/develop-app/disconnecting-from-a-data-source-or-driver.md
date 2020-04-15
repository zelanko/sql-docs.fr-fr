---
title: Déconnecter d’une source de données ou d’un pilote Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300459"
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Déconnexion d’une source de données ou d’un pilote
Lorsqu’une application a terminé l’utilisation d’une source de données, elle appelle **SQLDisconnect**. **SQLDisconnect** libère toutes les déclarations qui sont attribuées sur la connexion et déconnecte le conducteur de la source de données. Il renvoie une erreur si une transaction est en cours.  
  
 Après la déconnexion, l’application peut appeler **SQLFreeHandle** pour libérer la connexion. Après avoir libéré la connexion, il s’agit d’une erreur de programmation d’application pour utiliser la poignée de la connexion dans un appel à une fonction ODBC; conséquences indéfinises mais probablement fatales. Lorsque **SQLFreeHandle** est appelé, le conducteur libère la structure utilisée pour stocker des informations sur la connexion.  
  
 L’application peut également réutiliser la connexion, soit pour se connecter à une source de données différente ou se reconnecter à la même source de données. La décision de rester connecté, plutôt que de se déconnecter et de se reconnecter plus tard, exige que l’auteur de la demande examine les coûts relatifs de chaque option; se connecter à une source de données et rester connectés peut être relativement coûteux en fonction du support de connexion. En effectuant un compromis correct, la demande doit également faire des hypothèses sur la probabilité et le calendrier des opérations ultérieures sur la même source de données.
