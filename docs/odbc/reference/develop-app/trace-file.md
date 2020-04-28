---
title: Fichier de trace | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298056"
---
# <a name="trace-file"></a>Fichier de trace
Une application spécifie le fichier de trace soit en définissant le mot clé **tracefile** dans l’entrée de Registre ODBC. ini, soit en appelant **SQLSetConnectAttr** avec l’attribut de connexion SQL_ATTR_TRACEFILE. Si le fichier n’existe pas lorsque le suivi est activé, le gestionnaire de pilotes crée le fichier. Chaque application doit avoir son propre fichier de trace dédié pour éviter la contention. Une application peut utiliser plusieurs fichiers de suivi ; le programme d’installation d’une application peut fournir à l’utilisateur un choix de fichiers de trace. Si le suivi est activé de manière dynamique, une application peut également afficher les résultats de la trace plutôt que d’enregistrer dans le fichier de trace.  
  
 Le fichier de trace fournit un journal de chaque appel de fonction ODBC avec les types de données et les valeurs de tous les arguments. Il journalise toutes les fonctions d’entrée et journalise toutes les fonctions retournées avec les codes de retour et les États d’erreur.  
  
 Dans ODBC *3. x*, les paramètres des fonctions de connexion ne sont pas fournis à la dll de trace.
