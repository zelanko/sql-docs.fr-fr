---
title: IRowsetFastLoad (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: feea17329a8e809083263a83217aeb87fbf91bc3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307241"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  L’interface **IRowsetFastLoad** expose la prise en charge des opérations de copie en bloc basées sur mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Les consommateurs de fournisseurs OLE DB Native Client utilisent l’interface pour ajouter rapidement des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à une table existante.  
  
 Si vous affectez la valeur VARIANT_TRUE à SSPROP_ENABLEFASTLOAD pour une session, vous ne pouvez pas lire les données des ensembles de lignes retournés ultérieurement à partir de cette session. Lorsque SSPROP_ENABLEFASTLOAD a la valeur VARIANT_TRUE, tous les ensembles de lignes créés sur la session sont du type IRowsetFastLoad. Les ensembles de lignes IRowsetFastLoad ne prennent pas en charge la fonctionnalité de récupération (fetch) des ensembles de lignes. Par conséquent, les données issues de ces ensembles de lignes ne peuvent pas être lues.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md)|Marque la fin d'un lot de lignes insérées et écrit les lignes dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|Ajoute une ligne à l'ensemble de lignes de copie en bloc.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Copier des données en bloc à l’aide de IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Envoyer des données BLOB vers SQL SERVER en utilisant IROWSETFASTLOAD et ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
