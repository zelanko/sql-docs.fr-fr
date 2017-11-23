---
title: Pilote PHP pour SQL Server Support for LocalDB | Documents Microsoft
ms.custom: 
ms.date: 02/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: abf75fb674ea8da86c84c3605dadef61db8b3913
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="php-driver-for-sql-server-support-for-localdb"></a>Prise en charge de LocalDB par le pilote SQL Server pour PHP

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

À compter de [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)], une version légère de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], appelée LocalDB, sera disponible. Cette rubrique explique comment se connecter à une base de données dans une instance LocalDB.

## <a name="remarks"></a>Notes

Pour plus d’informations sur la base de données locale, y compris comment installer LocalDB et configurer votre instance de base de données locale, consultez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] rubrique de la documentation en ligne sur [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Express LocalDB.

Pour résumer, LocalDB vous permet d'effectuer les opérations suivantes :

-   Utiliser **sqllocaldb.exe i** pour déterminer le nom de l'instance par défaut.

-   Utiliser le mot clé de chaîne de connexion **AttachDBFilename** pour spécifier le fichier de base de données auquel le serveur doit se rattacher. Lorsque vous utilisez **AttachDBFilename**, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion **Database** , la base de données est supprimée de l'instance LocalDB lorsque l'application se ferme.

-   Spécifiez une instance de la base de données locale dans votre chaîne de connexion. Par exemple, Voici un exemple de chaîne de connexion SQLSRV :

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    L’élément suivant est un exemple de chaîne de connexion PDO_SQLSRV :  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

Si nécessaire, vous pouvez créer une instance LocalDB avec sqllocaldb.exe. Vous pouvez également utiliser sqlcmd.exe pour ajouter et modifier des bases de données dans une instance LocalDB. Par exemple, `sqlcmd -S (localdb)\v11.0`. (Lors de l’exécution dans IIS, vous devez exécuter sous le compte approprié pour obtenir les mêmes résultats que lorsque vous exécutez à la ligne de commande, consultez [à l’aide de LocalDB avec IIS complet, partie 2 : la propriété d’Instance](http://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx) pour plus d’informations.)

Chaînes de connexion exemple à l’aide du pilote SQLSRV qui se connectent à une base de données dans une base de données locale d’une instance appelée myInstance nommée sont les suivants :

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

Chaînes de connexion exemple à l’aide du pilote PDO_SQLSRV qui se connectent à une base de données dans une base de données locale d’une instance appelée myInstance nommée sont les suivants :  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

Vous pouvez télécharger LocalDB depuis le [page de pack de fonctionnalités de SQL Server 2012](http://go.microsoft.com/fwlink/?LinkID=236805), ou à partir de la [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Express edition. Si vous devez utiliser sqlcmd.exe pour modifier les données dans votre instance de base de données locale, vous aurez besoin de sqlcmd à partir de [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)], que vous pouvez obtenir à partir du téléchargement des utilitaires de ligne de commande dans le [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] page Feature Pack.

## <a name="see-also"></a>Voir aussi

[Connexion au serveur](../../connect/php/connecting-to-the-server.md)
