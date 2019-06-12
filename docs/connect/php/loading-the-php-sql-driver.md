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
manager: jroth
ms.openlocfilehash: 4b2f02fc81b969f8633a5a951483745c1d2635b0
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799634"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Chargement des pilotes Microsoft SQL Server pour PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique fournit des instructions pour le chargement de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] dans l’espace de processus PHP.  
  
Vous pouvez télécharger les pilotes prédéfinis pour votre plateforme depuis le [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) page de projet Github. Chaque package d’installation contient les fichiers de pilote SQLSRV et PDO_SQLSRV dans des variantes et non-thread. Sur Windows, elles sont également disponibles dans des variantes 32 bits et 64 bits. Consultez [configuration système requise pour le Microsoft Drivers for PHP for SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md) pour obtenir la liste des fichiers de pilote qui sont contenus dans chaque package. Le fichier de pilote doit correspondre à la version PHP, l’architecture et threadedness de votre environnement de PHP.

Sur Linux et macOS, les pilotes peuvent également être installés à l’aide de PECL, tel que figurant dans le [didacticiel d’installation](../../connect/php/installation-tutorial-linux-mac.md).

Vous pouvez également créer les pilotes à partir de la source lors de la génération de PHP ou à l’aide de `phpize`. Si vous choisissez de générer les pilotes à partir de la source, vous avez la possibilité de les créer statiquement dans PHP au lieu de les créer des extensions comme étant partagées en ajoutant `--enable-sqlsrv=static --with-pdo_sqlsrv=static` (sur Linux et macOS) ou `--enable-sqlsrv=static --with-pdo-sqlsrv=static` (sur Windows) pour le `./configure` commande quand Création de PHP. Pour plus d’informations sur le PHP le système de génération et `phpize`, consultez le [documentation PHP](http://php.net/manual/install.php).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Déplacement du fichier de pilote dans votre répertoire d’extension  
Le fichier de pilote doit se trouver dans un répertoire où le runtime PHP peut le trouver. Il est plus facile de placer le fichier de pilote dans votre répertoire d’extensions PHP par défaut - pour trouver le répertoire par défaut, exécutez `php -i | sls extension_dir` sur Windows ou `php -i | grep extension_dir` sur Linux/Mac OS. Si vous n’utilisez pas le répertoire d’extension par défaut, spécifiez un répertoire dans le fichier de configuration PHP (php.ini), à l’aide de la **extension_dir** option. Par exemple, sur Windows, si vous avez placé le fichier de pilote dans votre `c:\php\ext` directory, ajoutez la ligne suivante au fichier php.ini :
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Chargement du pilote au démarrage de PHP  
Pour charger le pilote SQLSRV au démarrage de PHP, commencez par déplacer un fichier de pilote dans votre répertoire d’extension. Ensuite, procédez comme suit :  
  
1.  Pour activer la **SQLSRV** pilote, modifier **php.ini** en ajoutant la ligne suivante à la section d’extension, modifier le nom de fichier comme il convient :  
  
    Sur Windows : 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    Sur Linux, si vous avez téléchargé les fichiers binaires prédéfinis pour votre distribution : 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Si vous avez compilé le SQLSRV binaire à partir de la source ou avec PECL, il sera à la place nommé sqlsrv.so :
    ```
    extension=sqlsrv.so
    ```
  
2.  Pour activer la **PDO_SQLSRV** pilote, l’extension des objets de données PHP (AOP) doit être disponible, une extension intégrée, soit comme une extension chargée dynamiquement.

    Sur Windows, les fichiers binaires PHP prédéfinis sont fournis avec PDO intégré, il est donc inutile de modifier le fichier php.ini pour charger. Si, toutefois, vous avez compilé PHP à partir de la source et spécifié une extension PDO distincte à générer, il sera nommé `php_pdo.dll`, et vous devez les copier dans votre répertoire d’extension et ajoutez la ligne suivante au fichier php.ini :  
    ```
    extension=php_pdo.dll  
    ```
    Sur Linux, si vous avez installé PHP à l’aide du Gestionnaire de package de votre système, PDO est probablement installé comme une extension chargée dynamiquement nommée pdo.so. L’extension PDO doit être chargée avant l’extension PDO_SQLSRV, ou le chargement échoue. Les extensions sont généralement chargées à l’aide de fichiers .ini individuels, et ces fichiers sont lus après php.ini. Par conséquent, si pdo.so est chargé par le biais de son propre fichier .ini, un fichier distinct du chargement du pilote PDO_SQLSRV après PDO est requis. 

    Pour déterminer le répertoire dans lequel sont situés les fichiers spécifiques à l’extension .ini, exécutez `php --ini` et notez le répertoire affiché sous `Scan for additional .ini files in:`. Recherchez le fichier qui charge pdo.so--il est probablement préfixé par un nombre, tel que 10-pdo.ini. Le préfixe numérique indique l’ordre de chargement des fichiers .ini, tandis que les fichiers qui n’ont pas un préfixe numérique sont chargés par ordre alphabétique. Créez un fichier pour charger le fichier de pilote PDO_SQLSRV appelé 30-pdo_sqlsrv.ini (tout nombre supérieur à celui qui sert de préfixe pdo.ini works) ou pdo_sqlsrv.ini (si pdo.ini n’est pas précédé d’un nombre) et ajoutez la ligne suivante, en modifiant le nom de fichier en tant que appropriées :  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Comme avec SQLSRV, si vous avez compilé le PDO_SQLSRV binaire à partir de la source ou avec PECL, il sera à la place nommé pdo_sqlsrv.so :
    ```
    extension=pdo_sqlsrv.so
    ```
    Copiez ce fichier dans le répertoire qui contient les autres fichiers .ini. 

    Si vous avez compilé PHP à partir de la source avec une prise en charge PDO intégrée, vous n’avez pas besoin d’un fichier .ini distinct, et vous pouvez ajouter la ligne appropriée ci-dessus à php.ini.
  
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
  
