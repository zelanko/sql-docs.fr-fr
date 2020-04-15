---
title: Bound vs Unbound Text and Image Columns (fr) Microsoft Docs
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
ms.openlocfilehash: 0cfa05f7019342d63ab6f3092c3b6df5ae6e8daa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297732"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Colonnes de texte et d'image liées et non liées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lors de l’utilisation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de curseurs serveur, le pilote Native Client ODBC est optimisé pour ne pas transmettre les données pour le **texte**non lié, **ntext**, ou colonnes **d’image** au moment **SQLFetch** est effectué. Le **texte**, **ntext**, ou les données **d’image** n’est pas réellement récupéré à partir du serveur jusqu’à ce que l’application émet [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) pour la colonne.  
  
 De nombreuses applications peuvent être écrites de sorte qu’aucun **texte,** **ntext**, ou des données **d’image** est affiché alors qu’un utilisateur est tout simplement défiler de haut en bas dans un curseur. Lorsqu’un utilisateur sélectionne une ligne pour obtenir plus de détails, l’application peut alors appeler **SQLGetData** pour récupérer le **texte,** **le ntext**, ou les données **d’image.** Cela empêchera la transmission du **texte,** **du ntext**, ou des données **d’image** pour l’une des lignes que l’utilisateur ne sélectionne pas, et peut donc empêcher la transmission de très grandes quantités de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes de texte et d’image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Comportements des curseurs](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
