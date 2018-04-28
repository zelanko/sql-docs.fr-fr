---
title: Prise en charge FILESTREAM (OLE DB) | Documents Microsoft
description: Prise en charge de FILESTREAM (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB [FILESTREAM support]
- FILESTREAM [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: efbe3ce15444b0c6556cf3cef0267e99bb55657f
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2018
---
# <a name="filestream-support-ole-db"></a>Prise en charge de FILESTREAM (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  À partir de [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] et pilote OLE DB pour SQL Server, OLE DB prend en charge la fonctionnalité FILESTREAM améliorée. Pour plus d’informations sur cette fonctionnalité, consultez [prise en charge FILESTREAM](../../oledb/features/filestream-support.md). Pour obtenir des exemples, consultez [Filestream et OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  
  
 Pour envoyer et recevoir **varbinary (max)** une valeur supérieure à 2 Go, une application utilise **DBTYPE_IUNKNOWN** dans les liaisons de paramètres et les résultats. Pour les paramètres du fournisseur doit appeler IUnknown::QueryInterface pour ISequentialStream et pour les résultats qui retournent ISequentialStream.  
  
 Pour OLE DB, la vérification associées aux valeurs de ISequentialStream sera levée. Lorsque *wType* est **DBTYPE_IUNKNOWN** dans le **DBBINDING** struct, la vérification de la longueur peut être désactivée en omettant **DBPART_LENGTH** de *dwPart* ou en définissant la longueur des données (à l’offset *obLength* dans le tampon de données) à ~ 0. Dans ce cas, le fournisseur ne vérifiera pas la longueur de la valeur et demandera et retournera toutes les données disponibles par le biais du flux de données. Cette modification sera appliquée à tous les types d'objets volumineux (LOB) et XML, mais uniquement en cas de connexion à des serveurs [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (ou ultérieurs). Cela offrira une plus grande souplesse aux développeurs, tout en maintenant la cohérence et la compatibilité descendante des applications existantes et des serveurs de niveau inférieur.  
  
 Cette modification affecte toutes les interfaces qui transfèrent des données, principalement IRowset::GetData ICommand::Execute et IRowsetFastLoad::InsertRow.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/oledb-driver-for-sql-server-programming.md)  
  
  
