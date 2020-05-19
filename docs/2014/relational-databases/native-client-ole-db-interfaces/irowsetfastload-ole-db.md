---
title: IRowsetFastLoad (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 720ea095343abefb0b56f4f1f47bbd853d72378e
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707342"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
  L' `IRowsetFastLoad` interface expose la prise en charge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] opérations de copie en bloc basées sur la mémoire. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Les consommateurs de fournisseurs OLE DB Native Client utilisent l’interface pour ajouter rapidement des données à une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table existante.  
  
 Si vous affectez la valeur VARIANT_TRUE à SSPROP_ENABLEFASTLOAD pour une session, vous ne pouvez pas lire les données des ensembles de lignes retournés ultérieurement à partir de cette session. Lorsque SSPROP_ENABLEFASTLOAD a la valeur VARIANT_TRUE, tous les ensembles de lignes créés sur la session sont du type IRowsetFastLoad. Les ensembles de lignes IRowsetFastLoad ne prennent pas en charge la fonctionnalité de récupération (fetch) des ensembles de lignes. Par conséquent, les données issues de ces ensembles de lignes ne peuvent pas être lues.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](irowsetfastload-commit-ole-db.md)|Marque la fin d'un lot de lignes insérées et écrit les lignes dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](irowsetfastload-insertrow-ole-db.md)|Ajoute une ligne à l'ensemble de lignes de copie en bloc.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Copier des données en bloc à l’aide de IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Envoyer des données BLOB vers SQL SERVER en utilisant IROWSETFASTLOAD et ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
