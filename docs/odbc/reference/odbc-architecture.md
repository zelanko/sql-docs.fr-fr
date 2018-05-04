---
title: Architecture ODBC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59076df0044feea340c54df8af78bc286afba96b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
