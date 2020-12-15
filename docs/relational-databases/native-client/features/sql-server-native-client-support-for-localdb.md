---
title: Prise en charge de la base de données locale
description: Découvrez comment vous connecter à une base de données dans une instance de base de données locale, qui est une version allégée de SQL Server qui est prise en charge par SQL Server Native Client.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5a971836cd6b3dce74debb9ee0f150f6d8e20e6b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97462030"
---
# <a name="sql-server-native-client-support-for-localdb"></a>Prise en charge de SQL Server Native Client pour LocalDB
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  À compter de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], une version légère de SQL Server, appelée LocalDB, sera disponible. Cette rubrique explique comment se connecter à une base de données dans une instance LocalDB.  
  
## <a name="remarks"></a>Notes  
 Pour plus d'informations sur LocalDB, notamment comment installer LocalDB et configurer votre instance LocalDB, consultez :  
  
-   [Référence SQL Server Express LocalDB](../../../relational-databases/sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2016 Express LocalDB](../../../database-engine/configure-windows/sql-server-express-localdb.md)  
  
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
  
