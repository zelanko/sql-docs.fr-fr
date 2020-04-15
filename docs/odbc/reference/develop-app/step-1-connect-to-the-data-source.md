---
title: 'Étape 1 : Connectez-vous à la source de données Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a104733c0e5ec5acc87eeabd00c4e51d4bfd000
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301349"
---
# <a name="step-1-connect-to-the-data-source"></a>Étape 1 : Se connecter à la source de données
La première étape de toute application consiste à se connecter à la source de données. Cette phase, y compris les fonctions dont elle a besoin, est indiquée dans l’illustration suivante.  
  
 ![Connexion à la source de données dans une application ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 La première étape dans la connexion à la source de données est de charger le gestionnaire de conducteur et d’allouer la poignée de l’environnement avec **SQLAllocHandle**. Pour plus d’informations, voir [Allocating the Environment Handle](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 L’application enregistre ensuite la version d’ODBC à laquelle elle se conforme en appelant **SQLSetEnvAttr** avec l’attribut SQL_ATTR_APP_ODBC_VER environnement. Pour plus d’informations, voir [Décerlarons la version ODBC de l’application](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) et [la compatibilité et la conformité rétrograde aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Ensuite, l’application alloue une poignée de connexion avec **SQLAllocHandle** et se connecte à la source de données avec **SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**. Pour plus d’informations, voir [Allouer une poignée de connexion](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) et établir une [connexion](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 L’application définit ensuite tous les attributs de connexion, tels que l’opportunité de valider manuellement les transactions. Pour plus d’informations, voir [Attributs de connexion](../../../odbc/reference/develop-app/connection-attributes.md).
