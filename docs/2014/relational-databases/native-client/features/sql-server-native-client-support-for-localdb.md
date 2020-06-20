---
title: Prise en charge SQL Server Native Client pour la base de données locale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
author: rothja
ms.author: jroth
ms.openlocfilehash: d1adfcc0beba3b06028ddf4e4c7ddc6ca44faae9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011161"
---
# <a name="sql-server-native-client-support-for-localdb"></a>Prise en charge de SQL Server Native Client pour LocalDB
  À compter de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], une version légère de SQL Server, appelée LocalDB, sera disponible. Cette rubrique explique comment se connecter à une base de données dans une instance LocalDB.  
  
## <a name="remarks"></a>Notes  
 Pour plus d'informations sur LocalDB, notamment comment installer LocalDB et configurer votre instance LocalDB, consultez :  
  
-   [Référence SQL Server Express LocalDB](../../sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2014 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 Pour résumer, LocalDB vous permet d'effectuer les opérations suivantes :  
  
-   Utiliser `sqllocaldb.exe i` pour déterminer le nom de l'instance par défaut.  
  
-   Utiliser le mot clé de chaîne de connexion `AttachDBFilename` pour spécifier le fichier de base de données auquel le serveur doit se rattacher. Lorsque `AttachDBFilename` vous utilisez, si vous ne spécifiez pas le nom de la base de données avec le mot clé **de chaîne de connexion de base de données** , la base de données est supprimée de l’instance de base de données locale lorsque l’application se ferme.  
  
-   Spécifiez une instance LocalDB dans votre chaîne de connexion :  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 Si nécessaire, vous pouvez créer une instance LocalDB avec sqllocaldb.exe. Vous pouvez également utiliser sqlcmd.exe pour ajouter et modifier des bases de données dans une instance LocalDB. Par exemple : `sqlcmd -S (localdb)\v11.0`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)  
  
  
