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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936383"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Chargement des pilotes Microsoft SQL Server pour PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique fournit des instructions pour le chargement de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] dans l’espace de processus PHP.  
  
Vous pouvez télécharger les pilotes prédéfinis pour votre plateforme à partir de la page de projet [Microsoft drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) github. Chaque package d’installation contient des fichiers de pilote SQLSRV et PDO_SQLSRV dans des variantes de thread et non thread. Sur Windows, elles sont également disponibles en variantes 32 bits et 64 bits. Consultez [Configuration système requise pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md) pour obtenir la liste des fichiers de pilote contenus dans chaque package. Le fichier de pilote doit correspondre à la version PHP, à l’architecture et à la threadedness de votre environnement PHP.

Sur Linux et macOS, les pilotes peuvent également être installés à l’aide de PECL, comme indiqué dans le [didacticiel d’installation](../../connect/php/installation-tutorial-linux-mac.md).

Vous pouvez également générer les pilotes à partir de la source lors de la génération `phpize`de PHP ou à l’aide de. Si vous choisissez de générer les pilotes à partir de la source, vous avez la possibilité de les créer de manière statique dans php au lieu de les créer `--enable-sqlsrv=static --with-pdo_sqlsrv=static` en tant qu’extensions partagées en `--enable-sqlsrv=static --with-pdo-sqlsrv=static` ajoutant (sur Linux et MacOS `./configure` ) ou (sur Windows) à la commande lorsque génération de PHP. Pour plus d’informations sur le système de génération `phpize`php et, consultez la [documentation de php](http://php.net/manual/install.php).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Déplacement du fichier de pilote dans votre répertoire d’extension  
Le fichier de pilote doit se trouver dans un répertoire où le runtime PHP peut le trouver. Il est plus facile de placer le fichier de pilote dans votre répertoire d’extension php par défaut pour rechercher le répertoire `php -i | sls extension_dir` par défaut, `php -i | grep extension_dir` exécuter sur Windows ou sur Linux/MacOS. Si vous n’utilisez pas le répertoire d’extension par défaut, spécifiez un répertoire dans le fichier de configuration PHP (php. ini) à l’aide de l’option **extension_dir** Par exemple, sur Windows, si vous avez placé le fichier de pilote dans `c:\php\ext` votre répertoire, ajoutez la ligne suivante à php. ini:
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Chargement du pilote au démarrage de PHP  
Pour charger le pilote SQLSRV au démarrage de PHP, commencez par déplacer un fichier de pilote dans votre répertoire d’extension. Ensuite, procédez comme suit :  
  
1.  Pour activer le pilote **sqlsrv** , modifiez **php. ini** en ajoutant la ligne suivante à la section extension, en modifiant le nom de fichier comme il convient:  
  
    Sur Windows : 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    Sur Linux, si vous avez téléchargé les fichiers binaires prédéfinis pour votre distribution: 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Si vous avez compilé le binaire SQLSRV à partir de la source ou avec PECL, il sera nommé sqlsrv.so:
    ```
    extension=sqlsrv.so
    ```
  
2.  Pour activer le pilote **PDO_SQLSRV** , l’extension PDO (PHP Data Objects) doit être disponible, soit en tant qu’extension intégrée, soit en tant qu’extension chargée dynamiquement.

    Sur Windows, les fichiers binaires PHP prédéfinis sont fournis avec PDO intégré. il n’est donc pas nécessaire de modifier php. ini pour le charger. Toutefois, si vous avez compilé php à partir de la source et spécifié une extension PDO distincte à générer, elle est nommée `php_pdo.dll`et vous devez la copier dans votre répertoire d’extension et ajouter la ligne suivante à php. ini:  
    ```
    extension=php_pdo.dll  
    ```
    Sur Linux, si vous avez installé PHP à l’aide du gestionnaire de package de votre système, PDO est probablement installé comme une extension chargée dynamiquement nommée pdo.so. L’extension PDO doit être chargée avant l’extension PDO_SQLSRV, sinon le chargement échoue. Les extensions sont généralement chargées à l’aide de fichiers. ini individuels, et ces fichiers sont lus après php. ini. Par conséquent, si pdo.so est chargé par le biais de son propre fichier. ini, un fichier distinct chargeant le pilote PDO_SQLSRV après PDO est requis. 

    Pour déterminer le répertoire dans lequel se trouvent les fichiers. ini spécifiques à l’extension `php --ini` , exécutez et notez le répertoire `Scan for additional .ini files in:`répertorié sous. Recherchez le fichier qui charge pdo.so--il est probablement préfixé par un nombre, tel que 10-PDO. ini. Le préfixe numérique indique l’ordre de chargement des fichiers. ini, alors que les fichiers qui n’ont pas de préfixe numérique sont chargés par ordre alphabétique. Créez un fichier pour charger le fichier de pilote PDO_SQLSRV appelé 30-pdo_sqlsrv. ini (tout nombre supérieur à celui utilisé par le préfixe PDO. ini) ou PDO_SQLSRV. ini (si PDO. ini n’est pas précédé d’un nombre), puis ajoutez la ligne suivante, en remplaçant le nom de fichier par pose  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Comme avec SQLSRV, si vous avez compilé le binaire PDO_SQLSRV à partir de la source ou avec PECL, il sera nommé PDO_SQLSRV. so:
    ```
    extension=pdo_sqlsrv.so
    ```
    Copiez ce fichier dans le répertoire qui contient les autres fichiers. ini. 

    Si vous avez compilé PHP à partir de la source avec la prise en charge de PDO intégrée, vous n’avez pas besoin d’un fichier. ini distinct et vous pouvez ajouter la ligne appropriée ci-dessus à php. ini.
  
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
  
