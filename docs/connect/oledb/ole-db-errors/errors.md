---
title: OLE DB Errors
description: Découvrez comment les erreurs sont retournées dans Microsoft OLE DB Driver pour SQL Server et comment obtenir des informations à leur sujet.
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddd8fd4e6280e49d924a0bf60f4d8a4900c114e4
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862001"
---
# <a name="errors"></a>Erreurs
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Les objets OLE/COM signalent les erreurs via le code de retour HRESULT des fonctions membres objets. Un valeur HRESULT OLE/COM est une structure de bits comprimée. OLE fournit des macros qui déréférencent les membres de la structure.  
  
 OLE/COM spécifie l’interface **IErrorInfo**. L’interface propose des méthodes comme **GetDescription**. Ceci permet aux clients d'extraire des informations détaillées sur les erreurs à partir des serveurs OLE/COM. OLE DB étend **IErrorInfo** pour prendre en charge le retour de plusieurs paquets d’informations d’erreur lors de l’exécution d’une fonction à un seul membre.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut retourner plusieurs erreurs. Une application peut récupérer les erreurs de serveur une par une en appelant [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) en combinaison avec ISQLErrorInfo et IErrorRecords.  
  
 Le pilote OLE DB pour SQL Server expose la valeur **IErrorInfo** améliorée par un enregistrement OLE DB, la valeur **ISQLErrorInfo** personnalisée et les interfaces d’objet erreur [ISQLServerErrorInfo](https://docs.microsoft.com/sql/connect/oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db?view=sql-server-ver15) spécifiques au fournisseur.  
  
 Pour plus d’informations sur le suivi des erreurs, consultez [Suivi de l’accès aux données](https://go.microsoft.com/fwlink/?LinkId=125805). Pour plus d’informations sur les améliorations du suivi des erreurs ajoutées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], consultez [Accès aux informations de diagnostic dans le journal des événements étendus](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Codes de retour](../../oledb/ole-db-errors/return-codes.md)  
  
-   [Informations dans les interfaces d’erreur](../../oledb/ole-db-errors/information-in-error-interfaces.md)  
  
-   [Détails des erreurs SQL Server](../../oledb/ole-db-errors/sql-server-error-detail.md)  
  
-   [Extraction des informations sur les erreurs](../../oledb/ole-db-errors/retrieving-error-information.md)  
  
-   [Résultats des messages SQL Server](../../oledb/ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
