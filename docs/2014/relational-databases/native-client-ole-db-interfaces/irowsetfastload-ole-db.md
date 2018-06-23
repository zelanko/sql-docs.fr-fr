---
title: IRowsetFastLoad (OLE DB) | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c6ed5ff1f3cb0d818a25c6bf2a8753e2bb806e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042439"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
  Le `IRowsetFastLoad` interface expose la prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] basé sur mémoire des opérations de copie en bloc. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Consommateurs du fournisseur OLE DB du Client natifs utilisent l’interface pour ajouter rapidement des données à un fichier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.  
  
 Si vous affectez la valeur VARIANT_TRUE à SSPROP_ENABLEFASTLOAD pour une session, vous ne pouvez pas lire les données des ensembles de lignes retournés ultérieurement à partir de cette session. Lorsque SSPROP_ENABLEFASTLOAD a la valeur VARIANT_TRUE, tous les ensembles de lignes créés sur la session sera de type IRowsetFastLoad. Ensembles de lignes iRowsetFastLoad ne prennent pas en charge les fonctionnalité d’extraction de lignes ; Par conséquent, les données à partir de ces ensembles de lignes ne peuvent pas être lues.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Méthode|Description|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](irowsetfastload-commit-ole-db.md)|Marque la fin d'un lot de lignes insérées et écrit les lignes dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](irowsetfastload-insertrow-ole-db.md)|Ajoute une ligne à l'ensemble de lignes de copie en bloc.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Copie de données à l’aide de IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Envoyer des données BLOB à SQL SERVER en utilisant IROWSETFASTLOAD et ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  