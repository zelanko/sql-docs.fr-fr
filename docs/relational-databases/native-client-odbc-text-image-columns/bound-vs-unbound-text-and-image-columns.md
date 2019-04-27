---
title: Colonnes de texte et d’image Détachées des colonnes Text et Image | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4e760707c97b9ac45d30b2d94163561324e60db5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62737993"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Colonnes de texte et d’image liées et non liées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Lors de l’utilisation de curseurs côté serveur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client est optimisé pour ne pas transmettre les données pour indépendant **texte**, **ntext**, ou **image** colonnes au niveau de la temps **SQLFetch** est effectuée. Le **texte**, **ntext**, ou **image** données ne sont pas réellement récupérées à partir du serveur jusqu'à ce que les problèmes des applications [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) pour le colonne.  
  
 De nombreuses applications peuvent être écrites afin qu’aucun **texte**, **ntext**, ou **image** données s’affiche pendant un utilisateur est simplement le défilement haut et le bas dans un curseur. Lorsqu’un utilisateur sélectionne une ligne pour obtenir plus de détails, l’application peut ensuite appeler **SQLGetData** pour récupérer le **texte**, **ntext**, ou **image** données. Cela évite de transmettre le **texte**, **ntext**, ou **image** données pour toutes les lignes de l’utilisateur sans sélectionner et peut par conséquent d’empêchent la transmission de très grande taille quantités de données.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des colonnes Text et Image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Comportements des curseurs](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
