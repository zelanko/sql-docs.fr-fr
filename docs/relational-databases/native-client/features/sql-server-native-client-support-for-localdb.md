---
title: SQL Server Native Client Support for LocalDB | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 24a29f830ae3feba4f2da02c38dff62b976dfa94
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-native-client-support-for-localdb"></a>Prise en charge de SQL Server Native Client pour LocalDB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  À compter de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], une version légère de SQL Server, appelée LocalDB, sera disponible. Cette rubrique explique comment se connecter à une base de données dans une instance LocalDB.  
  
## <a name="remarks"></a>Notes  
 Pour plus d'informations sur LocalDB, notamment comment installer LocalDB et configurer votre instance LocalDB, consultez :  
  
-   [Référence SQL Server Express LocalDB](../../../relational-databases/sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2016 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 Pour résumer, LocalDB vous permet d'effectuer les opérations suivantes :  
  
-   Utiliser **sqllocaldb.exe i** pour déterminer le nom de l'instance par défaut.  
  
-   Utiliser le mot clé de chaîne de connexion **AttachDBFilename** pour spécifier le fichier de base de données auquel le serveur doit se rattacher. Lorsque vous utilisez **AttachDBFilename**, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion **Database** , la base de données est supprimée de l'instance LocalDB lorsque l'application se ferme.  
  
-   Spécifiez une instance LocalDB dans votre chaîne de connexion :  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 Si nécessaire, vous pouvez créer une instance LocalDB avec sqllocaldb.exe. Vous pouvez également utiliser sqlcmd.exe pour ajouter et modifier des bases de données dans une instance LocalDB. Par exemple, **sqlcmd -S (localdb)\v11.0**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
