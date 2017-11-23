---
title: Fichier de trace | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 17820a03e062feb24e3b10e58cbcf29b3feb8ba3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="trace-file"></a>Fichier de trace
Une application spécifie le fichier de trace en définissant le **TraceFile** mot clé dans l’entrée de Registre Odbc.ini ou en appelant **SQLSetConnectAttr** avec l’attribut de connexion SQL_ATTR_TRACEFILE. Si le fichier n’existe pas lorsque le traçage est activé, le Gestionnaire de pilote va créer le fichier. Chaque application doit avoir son propre fichier de trace dédié pour éviter la contention. Une application peut utiliser plusieurs fichiers de trace ; programme d’installation d’une application peut fournir l’utilisateur avec un choix de fichiers de trace. Si le traçage est activé de manière dynamique, une application peut également afficher les résultats de trace, plutôt que la journalisation dans le fichier de trace.  
  
 Le fichier de trace fournit un journal de chaque appel de fonction ODBC avec les types de données et les valeurs de tous les arguments. Il enregistre l’entrée de toutes les fonctions et enregistre toutes les fonctions retournées avec les codes de retour et les États d’erreur.  
  
 Dans ODBC 3*.x*, les paramètres à des fonctions de connexion ne sont pas fournies à la DLL de trace.
