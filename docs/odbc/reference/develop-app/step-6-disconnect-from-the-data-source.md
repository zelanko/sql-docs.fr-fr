---
title: 'Étape 6 : Déconnectez-vous de la source de données Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df8cd94435d74bf813b0b64be0753a0beb44d354
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302790"
---
# <a name="step-6-disconnect-from-the-data-source"></a>Étape 6 : Se déconnecter de la source de données
La dernière étape consiste à se déconnecter de la source de données, comme le montre l’illustration suivante. Tout d’abord, l’application libère toute poignée de déclaration en appelant **SQLFreeHandle**. Pour plus d’informations, voir [Libérer une poignée de déclaration](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Présente la déconnexion d'une source de données](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Ensuite, l’application se déconnecte de la source de données avec **SQLDisconnect** et libère la poignée de connexion avec **SQLFreeHandle**. Pour plus d’informations, voir [Déconnexion d’une source de données ou d’un pilote](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Enfin, l’application libère la poignée de l’environnement avec **SQLFreeHandle** et décharge le Driver Manager. Pour plus d’informations, voir [Allocating the Environment Handle](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
