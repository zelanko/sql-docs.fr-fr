---
title: Prise en charge par SqlClient de LocalDB
description: Décrit la prise en charge par SqlClient des bases de données LocalDB.
ms.date: 08/15/2019
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 4760e4928421e0acdeca22f31a00cb148b82019c
ms.sourcegitcommit: 49ee3d388ddb52ed9cf78d42cff7797ad6d668f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94384368"
---
# <a name="sqlclient-support-for-localdb"></a>Prise en charge par SqlClient de LocalDB

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

À compter du nom de code SQL Server Denali, une version légère de SQL Server, appelée LocalDB, sera disponible. Cette rubrique explique comment se connecter à une base de données LocalDB.  
  
## <a name="remarks"></a>Notes  
Pour plus d’informations sur LocalDB, notamment comment installer LocalDB et configurer votre instance LocalDB, consultez la Documentation en ligne de SQL Server.  
  
Pour résumer ce que vous pouvez faire avec LocalDB :  
  
- Créez et démarrez des instances de LocalDB avec sqllocaldb.exe ou votre fichier app.config.  
  
- Utilisez sqlcmd.exe pour ajouter et modifier des bases de données dans une instance LocalDB. Par exemple : `sqlcmd -S (localdb)\myinst`.  
  
- Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour ajouter une base de données à votre instance LocalDB. Quand vous utilisez `AttachDBFilename`, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion `Database`, la base de données est supprimée de l’instance LocalDB quand l’application se ferme.  
  
- Spécifiez une instance LocalDB dans votre chaîne de connexion. Par exemple, si le nom de votre instance est `myInstance`, la chaîne de connexion inclut les éléments suivants :  
  
```console
server=(localdb)\\myInstance  
```  
  
`User Instance=True` n’est pas autorisé lors de la connexion à une base de données LocalDB.  
  
Vous pouvez télécharger LocalDB à partir de [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/details.aspx?id=56041). Si vous devez utiliser sqlcmd.exe pour modifier des données dans votre instance de LocalDB, vous aurez besoin du sqlcmd de SQL Server 2012, que vous pouvez également obtenir dans SQL Server 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Créer par programme une instance nommée  
Une application peut créer une instance nommée et spécifier une base de données comme suit :  
  
- Spécifiez les instances LocalDB à créer dans le fichier app.config, comme suit.  Le numéro de version de l’instance doit être le même que le numéro de version de votre installation de LocalDB.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- Spécifiez le nom de l’instance à l’aide du mot clé de chaîne de connexion `server`.  Le nom de l’instance spécifié dans le mot clé de chaîne de connexion `server` doit correspondre au nom spécifié dans le fichier app.config.  
  
- Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour spécifier le fichier .MDF.  
  
## <a name="next-steps"></a>Étapes suivantes
- [Fonctionnalités de SQL Server et ADO.NET](sql-server-features-adonet.md)
