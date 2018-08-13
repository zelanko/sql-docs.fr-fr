---
title: À l’aide de la Clause OUTPUT avec OLE DB dans SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 53deeb99-c088-4fde-844b-b2d91d6de1eb
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 3decdc6727fd23d8e219b4edee5cc9290f8c5c9d
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39563123"
---
# <a name="using-the-output-clause-with-ole-db-in-sql-server-native-client"></a>Utilisation de la clause OUTPUT avec OLE DB dans SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Si vous utilisez une clause OUTPUT dans une commande INSERT, UPDATE, DELETE ou MERGE, le nombre de lignes affectées n’est pas disponible. L’application doit compter le nombre de lignes de l’ensemble de lignes retourné par la clause OUTPUT.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application de fournisseur OLE DB de SQL Server Native Client](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
