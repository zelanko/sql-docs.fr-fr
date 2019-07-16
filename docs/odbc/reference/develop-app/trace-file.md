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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c94c3718c116b37eb198264887dfb4a319bd1dc3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985152"
---
# <a name="trace-file"></a>Fichier de trace
Une application spécifie le fichier de trace en définissant le **TraceFile** mot clé dans l’entrée de Registre Odbc.ini ou en appelant **SQLSetConnectAttr** avec l’attribut de connexion SQL_ATTR_TRACEFILE. Si le fichier n’existe pas lorsque le traçage est activé, le Gestionnaire de pilote va créer le fichier. Chaque application doit avoir son propre fichier de trace dédié pour éviter la contention. Une application peut utiliser plusieurs fichiers de trace ; programme d’installation d’une application peut fournir l’utilisateur avec un choix de fichiers de trace. Si le traçage est activé dynamiquement, une application peut également afficher les résultats de trace, plutôt que la journalisation dans le fichier de trace.  
  
 Le fichier de trace fournit un journal de chaque appel de fonction ODBC avec les types de données et les valeurs de tous les arguments. Il enregistre l’entrée de toutes les fonctions et consigne toutes les fonctions retournées avec les codes de retour et les États d’erreur.  
  
 Dans ODBC *3.x*, paramètres aux fonctions de connexion ne sont pas fournis à la DLL de trace.
