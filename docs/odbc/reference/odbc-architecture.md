---
title: Architecture ODBC ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07435dc1a5fbe800f2260e914f315cfe93dd8d1b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305130"
---
# <a name="odbc-architecture"></a>Architecture d’ODBC
L’architecture ODBC comporte quatre volets :  
  
-   **Demande** Effectue le traitement et appelle les fonctions ODBC pour soumettre des relevés SQL et récupérer les résultats.  
  
-   **Gestionnaire de pilote** Charge et décharge les chauffeurs pour le compte d’une demande. Traite la fonction ODBC les appelle ou les transmet à un conducteur.  
  
-   **Pilote** Traite les appels de fonction ODBC, soumet des demandes SQL à une source de données spécifique et renvoie les résultats à la demande. Si nécessaire, le conducteur modifie la demande d’une demande afin que la demande soit conforme à la syntaxe supportée par le DBMS associé.  
  
-   **Source de données** Se compose des données que l’utilisateur veut accéder et de son système d’exploitation associé, DBMS, et la plate-forme réseau (le cas échéant) utilisé pour accéder à la DBMS.  
  
 Notez les points suivants sur l’architecture ODBC. Tout d’abord, plusieurs pilotes et sources de données peuvent exister, ce qui permet à l’application d’accéder simultanément aux données de plus d’une source de données. Deuxièmement, l’API ODBC est utilisé en deux endroits : entre l’application et le gestionnaire de conducteur, et entre le gestionnaire de conducteur et chaque conducteur. L’interface entre le Driver Manager et les pilotes est parfois appelée *l’interface fournisseur de services,* ou *SPI*. Pour ODBC, l’interface de programmation d’applications (API) et l’interface des fournisseurs de services (SPI) sont les mêmes; c’est-à-dire que le Driver Manager et chaque pilote ont la même interface aux mêmes fonctions.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Applications](../../odbc/reference/applications.md)  
  
-   [Le gestionnaire de pilotes](../../odbc/reference/the-driver-manager.md)  
  
-   [Pilotes](../../odbc/reference/drivers.md)  
  
-   [Sources de données](../../odbc/reference/data-sources.md)
