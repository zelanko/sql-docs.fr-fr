---
title: Erreurs | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5eb72a4ea0da5f9be0c08ec597ebc341cea1068e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773406"
---
# <a name="errors"></a>Erreurs
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Les objets OLE/COM signalent les erreurs via le code de retour HRESULT des fonctions membres objets. Un valeur HRESULT OLE/COM est une structure de bits comprimée. OLE fournit des macros qui déréférencent les membres de la structure.  
  
 OLE/COM spécifie l’interface **IErrorInfo**. L’interface propose des méthodes comme **GetDescription**. Ceci permet aux clients d'extraire des informations détaillées sur les erreurs à partir des serveurs OLE/COM. OLE DB étend **IErrorInfo** pour prendre en charge le retour de plusieurs paquets d’informations d’erreur lors de l’exécution d’une fonction à un seul membre.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner plusieurs erreurs. Une application peut récupérer les erreurs de serveur une par une en appelant [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) en combinaison avec ISQLErrorInfo et IErrorRecords.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client expose les OLE DB les interfaces **IErrorInfo**, les **ISQLErrorInfo**personnalisées et les interfaces d’objet d’erreur [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) spécifiques au fournisseur.  
  
 Pour plus d’informations sur le suivi des erreurs, consultez [Suivi de l’accès aux données](https://go.microsoft.com/fwlink/?LinkId=125805). Pour plus d’informations sur les améliorations du suivi des erreurs ajoutées dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], consultez [Accès aux informations de diagnostic dans le journal des événements étendus](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Codes de retour](../../relational-databases/native-client-ole-db-errors/return-codes.md)  
  
-   [Informations dans les interfaces d’erreur](../../relational-databases/native-client-ole-db-errors/information-in-error-interfaces.md)  
  
-   [Détails des erreurs SQL Server](../../relational-databases/native-client-ole-db-errors/sql-server-error-detail.md)  
  
-   [Extraction des informations sur les erreurs](../../relational-databases/native-client-ole-db-errors/retrieving-error-information.md)  
  
-   [Résultats des messages SQL Server](../../relational-databases/native-client-ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
