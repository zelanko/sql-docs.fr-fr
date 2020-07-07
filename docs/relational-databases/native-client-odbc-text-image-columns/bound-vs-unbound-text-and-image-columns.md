---
title: Colonnes de texte et d’image liées et non liées | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 11a7e27e7adce8f87986571c2029d37c82e319b3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012309"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Colonnes de texte et d'image liées et non liées
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Lors de l’utilisation de curseurs côté serveur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client est optimisé pour ne pas transmettre les données des colonnes de **texte**, **ntext**ou **image** non liées au moment où **SQLFetch** est exécutée. Les données **Text**, **ntext**ou **image** ne sont pas réellement récupérées à partir du serveur tant que l’application n’émet pas [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) pour la colonne.  
  
 De nombreuses applications peuvent être écrites de sorte qu’aucune donnée **Text**, **ntext**ou **image** ne soit affichée alors qu’un utilisateur fait simplement défiler la liste vers le haut et vers le haut dans un curseur. Lorsqu’un utilisateur sélectionne une ligne pour obtenir plus de détails, l’application peut ensuite appeler **SQLGetData** pour extraire les données **Text**, **ntext**ou **image** . Cela empêchera la transmission des données **Text**, **ntext**ou **image** pour les lignes que l’utilisateur ne sélectionne pas et peut donc empêcher la transmission de très grandes quantités de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Comportements des curseurs](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
