---
title: Chargement du pilote SQL PHP | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
caps.latest.revision: "42"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 90ba63857ea38481577083d2a85999e789dfcb84
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="loading-the-php-sql-driver"></a>Chargement du pilote SQL PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique fournit des instructions pour le chargement de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] dans l’espace de processus PHP.  
  
Deux options s’offrent à vous pour charger un pilote. Vous pouvez charger le pilote au démarrage de PHP ou au moment de l’exécution du script PHP.  
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Déplacement du fichier de pilote dans votre répertoire d’extension  
Quelle que soit la procédure utilisée, la première étape consiste à placer le fichier de pilote dans un répertoire où le runtime PHP peut le trouver. Placez alors le fichier de pilote dans votre répertoire d’extension PHP. Consultez [Configuration requise pour le pilote SQL PHP](../../connect/php/system-requirements-for-the-php-sql-driver.md) pour obtenir la liste des fichiers de pilote installés avec [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
Si nécessaire, spécifiez l’emplacement du répertoire du fichier de pilote dans le fichier de configuration PHP (php.ini), à l’aide de la **extension_dir** option. Par exemple, si vous placez le fichier de pilote dans votre répertoire c:\php\ext, utilisez cette option :  
  
```  
extension_dir = "c:\PHP\ext"  
```  
  
## <a name="loading-the-driver-at-php-startup"></a>Chargement du pilote au démarrage de PHP  
Pour charger [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] au démarrage de PHP, commencez par déplacer un fichier de pilote dans votre répertoire d’extension. Ensuite, procédez comme suit :  
  
1.  Pour activer la **SQLSRV** pilote, modifier **php.ini** en ajoutant la ligne suivante à la section d’extension, ou en modifiant la ligne qui existe déjà :  
  
    Sur Windows (cet exemple utilise la version 4.0 thread-safe du pilote pour PHP 7) : 
    ```  
    extension=php_sqlsrv_7_ts.dll  
    ```  
    Sur Linux (cet exemple utilise la version comme étant installé par PECL) : 
    ```  
    extension=sqlsrv.so  
    ```  
    Pour activer la **PDO_SQLSRV** pilote, modifier **php.ini** en ajoutant la ligne suivante à la section d’extension, ou en modifiant la ligne qui existe déjà :  
  
    Sur Windows (cet exemple utilise la version 4.0 thread-safe du pilote pour PHP 7) :
    ```  
    extension=php_pdo_sqlsrv_7_ts.dll  
    ```  
    Sur Linux (cet exemple utilise la version comme étant installé par PECL) :
    ```  
    extension=pdo_sqlsrv.so  
    ```  
  
2.  Si vous souhaitez utiliser le **PDO_SQLSRV** pilote, l’extension des objets de données PHP (PDO) doit être disponible, une extension intégrée, soit comme une extension chargée dynamiquement. Si vous devez charger le pilote PDO_SQLSRV dynamiquement, la bibliothèque php_pdo.dll (ou pdo.so sur Linux) doit être présent dans le répertoire d’extension et la ligne suivante doit se trouver dans le fichier php.ini :

    Sur Windows :  
    ```
    extension=php_pdo.dll  
    ```  
    Sur Linux :  
    ```
    extension=pdo.so  
    ```  
  
3.  Redémarrez le serveur web.  
  
> [!NOTE]  
> Pour déterminer si le pilote a été chargé avec succès, exécutez un script qui appelle [phpinfo()](http://go.microsoft.com/fwlink/?LinkId=108678).  
  
Pour plus d’informations sur les directives **php.ini** , consultez [Description des principales directives php.ini](http://go.microsoft.com/fwlink/?LinkId=105817).  
  
## <a name="loading-the-driver-at-php-script-runtime"></a>Chargement du pilote au moment de l’exécution du script PHP  
Pour charger [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] au moment de l’exécution du script, commencez par déplacer un fichier de pilote dans votre répertoire d’extension. Insérez ensuite la ligne suivante au début du script PHP qui correspond le nom de fichier du pilote :  
  
```  
dl('php_pdo_sqlsrv_7_ts.dll');  
```  
  
Pour plus d’informations sur les fonctions PHP liées au chargement dynamique des extensions, consultez [dl](http://go.microsoft.com/fwlink/?LinkId=105818) et [extension_loaded.](http://go.microsoft.com/fwlink/?LinkId=105819)  
  
## <a name="see-also"></a>Voir aussi  
[Prise en main du pilote SQL PHP](../../connect/php/getting-started-with-the-php-sql-driver.md)
[Configuration requise pour le pilote SQL PHP](../../connect/php/system-requirements-for-the-php-sql-driver.md)
[Guide de programmation pour le pilote SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  
