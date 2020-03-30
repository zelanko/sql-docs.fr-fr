---
title: Chargement de Microsoft Drivers for PHP for SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e3c6614425cf8796bd7ec462a62f9410b9ca5857
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67936383"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Chargement des pilotes Microsoft SQL Server pour PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique fournit des instructions pour le chargement de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] dans l’espace de processus PHP.  
  
Vous pouvez télécharger les pilotes prédéfinis pour votre plateforme sur la page de projet GitHub [Pilotes Microsoft pour PHP pour SQL Server](https://github.com/Microsoft/msphpsql/releases). Chaque package d’installation contient les fichiers de pilote SQLSRV et PDO_SQLSRV dans les variantes avec et sans thread. Sur Windows, ils sont également disponibles en version 32 bits et 64 bits. Pour obtenir la liste des fichiers de pilote contenus dans chaque package, consultez [Configuration système requise pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md). Le fichier de pilote doit correspondre à la version de PHP, à l’architecture et au type (avec/sans thread) de votre environnement PHP.

Sur Linux et macOS, les pilotes peuvent également être installés avec PECL, suivant le [tutoriel d’installation](../../connect/php/installation-tutorial-linux-mac.md).

Vous pouvez également générer les pilotes à partir de la source lors de l’étape de build de PHP ou avec `phpize`. Dans ce cas, vous aurez la possibilité de les créer de manière statique dans PHP, et non en tant qu’extensions partagées, en ajoutant `--enable-sqlsrv=static --with-pdo_sqlsrv=static` (sur Linux et macOS) ou `--enable-sqlsrv=static --with-pdo-sqlsrv=static` (sur Windows) à la commande `./configure` pendant l’étape de build de PHP. Pour plus d’informations sur le système de build de PHP et `phpize`, consultez la [Documentation de PHP](http://php.net/manual/install.php).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Déplacement du fichier de pilote dans votre répertoire d’extension  
Le fichier de pilote doit se trouver dans un répertoire accessible au runtime PHP. L’idéal est de le placer dans le répertoire par défaut de l’extension PHP ; pour trouver ce répertoire, exécutez `php -i | sls extension_dir` sur Windows ou `php -i | grep extension_dir` sur Linux/macOS. Si vous n’utilisez pas le répertoire d’extension par défaut, spécifiez un répertoire dans le fichier de configuration PHP (php.ini) avec l’option **extension_dir**. Par exemple, sur Windows, si vous avez placé le fichier de pilote dans votre répertoire `c:\php\ext`, ajoutez la ligne suivante à php.ini :
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Chargement du pilote au démarrage de PHP  
Pour charger le pilote SQLSRV au démarrage de PHP, commencez par déplacer un fichier de pilote dans votre répertoire d’extension. Ensuite, procédez comme suit :  
  
1.  Pour activer le pilote **SQLSRV**, modifiez **php.ini** en ajoutant la ligne suivante à la section extension, avec le nom de fichier correspondant :  
  
    Sur Windows : 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    Sur Linux, si vous avez téléchargé les binaires prédéfinis pour votre distribution : 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Si vous avez compilé le binaire SQLSRV à partir de la source ou avec PECL, il sera nommé sqlsrv.so :
    ```
    extension=sqlsrv.so
    ```
  
2.  Pour pouvoir activer le pilote **PDO_SQLSRV**, il est nécessaire que l’extension PDO (PHP Data Objects) soit disponible, soit comme extension intégrée, soit comme extension chargée dynamiquement.

    Sur Windows, l’extension PDO est intégrée dans les binaires PHP prédéfinis. Il n’est donc pas nécessaire de modifier php.ini pour la charger. Toutefois, si vous avez compilé le PHP à partir de la source et spécifié une extension PDO distincte à générer, elle sera nommée `php_pdo.dll`, et vous devrez la copier dans votre répertoire d’extension et ajouter la ligne suivante à php.ini :  
    ```
    extension=php_pdo.dll  
    ```
    Sur Linux, si vous avez installé PHP à l’aide du gestionnaire de package de votre système, l’extension PDO est probablement installée comme extension chargée dynamiquement sous le nom pdo.so. Elle doit être chargée avant l’extension PDO_SQLSRV, sinon le chargement échouera. Les extensions sont généralement chargées à l’aide de fichiers .ini individuels, qui sont lus après php.ini. Par conséquent, si pdo.so est chargé par le biais de son propre fichier .ini, un fichier distinct permettant de charger le pilote PDO_SQLSRV après PDO est nécessaire. 

    Pour savoir dans quel répertoire se trouvent les fichiers .ini de chaque extension, exécutez `php --ini` et notez le répertoire indiqué sous `Scan for additional .ini files in:`. Recherchez le fichier qui charge pdo.so : il est probablement préfixé par un nombre, par exemple 10-pdo.ini. Le préfixe numérique indique l’ordre de chargement des fichiers .ini, tandis que les fichiers dépourvus de préfixe numérique sont chargés par ordre alphabétique. Créez un fichier pour charger le fichier de pilote PDO_SQLSRV nommé 30-pdo_sqlsrv.ini (ou n’importe quel autre nombre supérieur au préfixe de pdo.ini) ou pdo_sqlsrv.ini (si pdo.ini n’est pas précédé d’un nombre), puis ajoutez la ligne suivante, avec le nom de fichier correspondant :  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Comme pour SQLSRV, si vous avez compilé le binaire PDO_SQLSRV à partir de la source ou avec PECL, il sera nommé pdo_sqlsrv.so :
    ```
    extension=pdo_sqlsrv.so
    ```
    Copiez ce fichier dans le répertoire contenant les autres fichiers .ini. 

    Si vous avez compilé PHP à partir de la source avec prise en charge intégrée de PDO, vous n’avez pas besoin d’un fichier .ini distinct et vous pouvez ajouter la ligne correspondante ci-dessus à php.ini.
  
3.  Redémarrez le serveur web.  
  
> [!NOTE]  
> Pour déterminer si le pilote a été correctement chargé, exécutez un script qui appelle [phpinfo()](https://php.net/manual/en/function.phpinfo.php).  
  
Pour plus d’informations sur les directives **php.ini**, consultez [Description des principales directives php.ini](https://php.net/manual/en/ini.core.php).  
  
## <a name="see-also"></a>Voir aussi  
[Bien démarrer avec les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Configuration système requise pour Microsoft Drivers for PHP for SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Référence API du pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
