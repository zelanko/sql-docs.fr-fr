---
title: Architecture ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83e35d58d180336c349e83c7991d27f7007aca4e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63273624"
---
# <a name="odbc-architecture"></a>Architecture d’ODBC
L’architecture ODBC possède quatre composants :  
  
-   **Application** effectue le traitement et les appels de fonctions ODBC pour envoyer des instructions SQL et de récupérer les résultats.  
  
-   **Gestionnaire de pilotes** charge et décharge les pilotes pour le compte d’une application. Processus (fonction ODBC) appelle ou les transmet à un pilote.  
  
-   **Pilote** (fonction ODBC) processus appelle, soumet des requêtes SQL à une source de données spécifique et retourne les résultats à l’application. Si nécessaire, le pilote modifie la requête d’une application afin que la demande est conforme à la syntaxe prise en charge par le SGBD associé.  
  
-   **Source de données** assure les données de l’utilisateur souhaite accéder et de son système d’exploitation associé, le SGBD, et la plate-forme réseau (le cas échéant) permettant d’accéder aux SGBD.  
  
 Notez les points suivants concernant l’architecture ODBC. Premier, plusieurs pilotes et sources de données peuvent exister, ce qui permet l’application d’accéder simultanément des données à partir de plusieurs sources de données. Deuxièmement, l’API ODBC est utilisé dans deux emplacements : entre l’application et le Gestionnaire de pilotes et entre le Gestionnaire de pilotes et de chaque pilote. L’interface entre le Gestionnaire de pilotes et les pilotes est parfois appelé le *interface du fournisseur de service,* ou *SPI*. Pour ODBC, l’application programming interface (API) et l’interface de fournisseur de service (SPI) sont les mêmes ; Autrement dit, le Gestionnaire de pilotes et chaque pilote ont la même interface pour les mêmes fonctions.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Applications](../../odbc/reference/applications.md)  
  
-   [Le gestionnaire de pilotes](../../odbc/reference/the-driver-manager.md)  
  
-   [Pilotes](../../odbc/reference/drivers.md)  
  
-   [Sources de données](../../odbc/reference/data-sources.md)
