---
title: Erreurs | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 82c45b91f4ac4f39a41467f46b0b031580f1b42a
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694930"
---
# <a name="errors"></a>Erreurs
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Les objets OLE/COM signalent les erreurs via le code de retour HRESULT des fonctions membres objets. Un valeur HRESULT OLE/COM est une structure de bits comprimée. OLE fournit des macros qui déréférencent les membres de la structure.  
  
 OLE/COM Spécifie le **IErrorInfo** interface. L’interface expose des méthodes telles que **GetDescription**. Ceci permet aux clients d'extraire des informations détaillées sur les erreurs à partir des serveurs OLE/COM. OLE DB étend **IErrorInfo** pour prendre en charge le retour de plusieurs paquets d’informations d’erreur sur l’exécution d’une fonction membre unique.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner plusieurs erreurs. Une application peut récupérer les erreurs de serveur une à la fois en appelant [IMultipleResults::GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) associée ISQLErrorInfo et IErrorRecords.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose OLE DB améliorée par un enregistrement **IErrorInfo**, personnalisé **ISQLErrorInfo**et spécifique au fournisseur [ISQLServerErrorInfo ](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaces objet d’erreur.  
  
 Pour plus d’informations sur le suivi des erreurs, consultez [suivi d’accès aux données](http://go.microsoft.com/fwlink/?LinkId=125805). Pour plus d’informations sur les améliorations apportées au suivi d’erreur ajouté dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], consultez [l’accès à des informations de Diagnostic dans le journal des événements étendus](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Codes de retour](../../relational-databases/native-client-ole-db-errors/return-codes.md)  
  
-   [Informations dans les interfaces d’erreur](../../relational-databases/native-client-ole-db-errors/information-in-error-interfaces.md)  
  
-   [Détails des erreurs SQL Server](../../relational-databases/native-client-ole-db-errors/sql-server-error-detail.md)  
  
-   [Extraction des informations sur les erreurs](../../relational-databases/native-client-ole-db-errors/retrieving-error-information.md)  
  
-   [Résultats des messages SQL Server](../../relational-databases/native-client-ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
