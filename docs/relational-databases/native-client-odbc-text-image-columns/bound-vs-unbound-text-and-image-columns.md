---
title: "Lié à Visual Studio. Indépendant des colonnes Text et Image | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-text-image-columns
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
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
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 44479d4350b43f4c38bf155d19ab03de19f8a159
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Lié à Visual Studio. Indépendant colonnes Text et Image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Lors de l’utilisation de curseurs côté serveur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client est optimisé pour ne pas transmettre les données pour indépendant **texte**, **ntext**, ou **image** colonnes au moment **SQLFetch** est effectuée. Le **texte**, **ntext**, ou **image** données ne sont pas réellement récupérées à partir du serveur jusqu'à ce que les problèmes des applications [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) pour la colonne.  
  
 De nombreuses applications peuvent être écrites afin qu’aucun **texte**, **ntext**, ou **image** données s’affiche lors d’un utilisateur est simplement le défilement haut et bas dans un curseur. Lorsqu’un utilisateur sélectionne une ligne pour obtenir plus de détails, l’application peut ensuite appeler **SQLGetData** pour récupérer le **texte**, **ntext**, ou **image** données. Cela évite de transmettre le **texte**, **ntext**, ou **image** les données de toutes les lignes de l’utilisateur ne pas sélectionner et peut par conséquent d’empêchent la transmission de très grandes quantités de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes Text et Image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Comportements des curseurs](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
