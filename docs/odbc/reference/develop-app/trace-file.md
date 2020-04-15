---
title: Fichier Trace Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddd0ee24649592cf4a1a296a51404334145a3bab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298056"
---
# <a name="trace-file"></a>Fichier de trace
Une application spécifie le fichier de trace soit en définissant le mot clé **TraceFile** dans la saisie du registre Odbc.ini ou en appelant **SQLSetConnectAttr** avec l’attribut de connexion SQL_ATTR_TRACEFILE. Si le fichier n’existe pas lorsque le traçage est activé, le gestionnaire de pilote créera le fichier. Chaque application doit avoir son propre fichier de trace dédié pour éviter toute contention. Une application peut utiliser plus d’un fichier de traces; le programme de configuration d’une application peut fournir à l’utilisateur un choix de fichiers de traces. Si le traçage est activé dynamiquement, une application peut également afficher des résultats de traces, plutôt que de vous connecter au fichier de traçage.  
  
 Le fichier de traces fournit un journal de chaque appel de fonction ODBC avec les types de données et les valeurs de tous les arguments. Il enregistre toutes les fonctions d’entrée et enregistre toutes les fonctions retournées avec des codes de retour et des états d’erreur.  
  
 Dans ODBC *3.x*, les paramètres aux fonctions de connexion ne sont pas fournis à la trace DLL.
