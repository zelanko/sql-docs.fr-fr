---
title: Architecture ODBC | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e1d59692492b2b14a51a8541e01d5e06a1a6d88
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-architecture"></a>Architecture ODBC
L’architecture ODBC possède quatre composants :  
  
-   **Application** effectue le traitement et les appels de fonctions ODBC pour envoyer des instructions SQL et extraire des résultats.  
  
-   **Gestionnaire de pilotes** charge et décharge les pilotes pour le compte d’une application. Processus (fonction ODBC) appelle ou les transmet à un pilote.  
  
-   **Pilote** fonction processus ODBC appelle, soumet les requêtes SQL à une source de données spécifique et retourne les résultats à l’application. Si nécessaire, le pilote modifie la requête d’une application afin que la demande est conforme à la syntaxe prise en charge par le SGBD associé.  
  
-   **Source de données** assure les données de l’utilisateur souhaite accéder et son système d’exploitation associé, SGBD, et la plateforme de réseau (le cas échéant) permet d’accéder aux SGBD.  
  
 Notez les points suivants concernant l’architecture ODBC. Premier, plusieurs pilotes et sources de données peuvent exister, ce qui permet à l’application d’accéder simultanément des données à partir de plusieurs sources de données. Ensuite, l’API ODBC est utilisé dans deux emplacements : entre l’application et le Gestionnaire de pilotes et entre le Gestionnaire de pilotes et de chaque pilote. L’interface entre le Gestionnaire de pilotes et les pilotes est parfois appelé le *interface du fournisseur de service,* ou *SPI*. Pour ODBC, l’application programming interface (API) et l’interface de fournisseur de service (SPI) sont identiques ; Autrement dit, le Gestionnaire de pilotes et chaque pilote ont la même interface pour les mêmes fonctions.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Applications](../../odbc/reference/applications.md)  
  
-   [Le gestionnaire de pilotes](../../odbc/reference/the-driver-manager.md)  
  
-   [Pilotes](../../odbc/reference/drivers.md)  
  
-   [Sources de données](../../odbc/reference/data-sources.md)
