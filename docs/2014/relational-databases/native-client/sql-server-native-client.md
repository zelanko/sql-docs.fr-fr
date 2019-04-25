---
title: Ce que&#39;s Nouveautés de SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2a01b9d9d13bf5e9135d287553beb8b87c2dcd5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62638845"
---
# <a name="what39s-new-in-sql-server-native-client"></a>Ce que&#39;s Nouveautés de SQL Server Native Client
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] installe [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client. Il n'y a pas de [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Native Client.  
  
 Il n'y aura plus de mises à jour vers le pilote ODBC dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Le successeur du pilote ODBC dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, appelé Pilote [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC 11 pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows, est installé avec [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Pour plus d’informations sur la [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows, consultez [Microsoft ODBC Driver 11 for SQL Server - Windows](https://www.microsoft.com/download/details.aspx?id=36434).  
  
 Le fournisseur OLE DB dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client a été mis à jour pour la dernière fois dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client. Les développeurs qui souhaitent utiliser un fournisseur OLE DB pour établir une connexion à la dernière version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent utiliser le fournisseur OLE DB distribué avec [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Native Client.  
  
 Les rubriques suivantes décrivent les nouvelles fonctionnalités significatives de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client présentes dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   [Prise en charge de SQL Server Native Client pour la base de données locale](features/sql-server-native-client-support-for-localdb.md)  
  
-   [Détection des métadonnées](features/metadata-discovery.md)  
  
-   [Prise en charge de UTF-16 dans SQL Server Native Client 11.0](features/utf-16-support-in-sql-server-native-client-11-0.md)  
  
-   [Prise en charge des fonctionnalités de récupération d'urgence, haute disponibilité par SQL Server Native Client](features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [Accès aux informations de diagnostic dans le journal des événements étendus](features/accessing-diagnostic-information-in-the-extended-events-log.md)  
  
 De plus, ODBC dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge maintenant trois fonctionnalités ajoutées à ODBC standard dans le kit de développement logiciel (SDK) Windows 7 :  
  
-   Exécution asynchrone sur les opérations relatives à une connexion. Pour plus d’informations, consultez [exécution asynchrone](https://go.microsoft.com/fwlink/?LinkID=191493).  
  
-   C. Extensibilité du type de données Pour plus d’informations, consultez [des Types de données C dans ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).  
  
     Pour prendre en charge cette fonctionnalité dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, SQLGetDescField peut retourner `SQL_C_SS_TIME2` (pour `time` types) ou `SQL_C_SS_TIMESTAMPOFFSET` (pour `datetimeoffset`) au lieu de `SQL_C_BINARY`, si votre application utilise ODBC 3.8. Pour plus d’informations, consultez [prise en charge du Type de données pour les améliorations ODBC Date / heure](features/date-and-time-improvements.md).  
  
-   Appel de `SQLGetData` à plusieurs reprises avec une petite mémoire tampon pour récupérer une valeur de paramètre élevée. Pour plus d’informations, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).  
  
 Les rubriques suivantes décrivent des changements de comportement de Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   Lors de l’appel `ICommandWithParameters::SetParameterInfo`, la valeur passée à la *pwszName* paramètre doit être un identificateur valide. Pour plus d’informations, consultez [ICommandWithParameters](../native-client-ole-db-interfaces/icommandwithparameters.md).  
  
-   `SQLDescribeParam` retourne maintenant de manière cohérente une valeur qui se conforme à la spécification ODBC. Pour plus d’informations, consultez [SQLDescribeParam](../native-client-odbc-api/sqldescribeparam.md).  
  
-   [Changement de comportement du pilote ODBC lors de la gestion des conversions de caractères](features/odbc-driver-behavior-change-when-handling-character-conversions.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](features/sql-server-native-client-features.md)  
  
  
