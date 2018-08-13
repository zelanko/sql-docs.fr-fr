---
title: Profilage des rubriques de procédures performances de pilote d’ODBC (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: ef057916d039d73681aaacb9f5642020e074e9d0
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39563423"
---
# <a name="profiling-odbc-driver-performance-odbc"></a>Profilage des données de performances du pilote ODBC (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a deux options spécifiques au pilote pour le profilage de performances du pilote.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC peut consigner les statistiques de performances dans le fichier. Le fichier journal est un fichier délimité par des tabulations qui peut être analysé dans toute application qui prend en charge les fichiers délimités par des tabulations, telle que Microsoft Excel.  
  
 Le pilote peut également enregistrer les requêtes longues (requêtes qui n'obtiennent pas de réponse du serveur dans un délai spécifié). Ces requêtes peuvent être analysées ultérieurement par les programmeurs et les administrateurs de base de données.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Profiler des données de performances du pilote &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data.md)  
  
-   [Journal des requêtes à Long terme &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures liées à ODBC](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
  
