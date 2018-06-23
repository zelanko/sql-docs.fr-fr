---
title: Erreurs | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a3210cb1cd48a375e428cc6cf8a40e6f76f48b21
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043839"
---
# <a name="errors"></a>Erreurs
  Les objets OLE/COM signalent les erreurs via le code de retour HRESULT des fonctions membres objets. Un valeur HRESULT OLE/COM est une structure de bits comprimée. OLE fournit des macros qui déréférencent les membres de la structure.  
  
 OLE/COM Spécifie le **IErrorInfo** interface. L’interface expose des méthodes telles que **GetDescription**. Ceci permet aux clients d'extraire des informations détaillées sur les erreurs à partir des serveurs OLE/COM. OLE DB étend **IErrorInfo** pour prendre en charge le retour de plusieurs paquets d’informations d’erreur sur l’exécution d’une fonction membre unique.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner plusieurs erreurs. Une application peut récupérer les erreurs de serveur une à la fois en appelant [IMultipleResults::GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) associée ISQLErrorInfo et IErrorRecords.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose OLE DB améliorée par un enregistrement **IErrorInfo**, personnalisé `ISQLErrorInfo`et spécifique au fournisseur [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) objet error interfaces.  
  
 Pour plus d’informations sur le suivi des erreurs, consultez [suivi d’accès aux données](http://go.microsoft.com/fwlink/?LinkId=125805). Pour plus d’informations sur les améliorations apportées au suivi d’erreur ajouté dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], consultez [l’accès à des informations de Diagnostic dans le journal des événements étendus](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Codes de retour](return-codes.md)  
  
-   [Informations dans les interfaces d’erreur](information-in-error-interfaces.md)  
  
-   [Détails des erreurs SQL Server](sql-server-error-detail.md)  
  
-   [Extraction des informations sur les erreurs](retrieving-error-information.md)  
  
-   [Résultats des messages SQL Server](sql-server-message-results.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  