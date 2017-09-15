---
title: "À propos des exemples de Code dans la Documentation | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d24d29aba9db9d3626a456f87f799e00da1b42cc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="about-code-examples-in-the-documentation"></a>À propos des exemples de code dans la documentation
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Il existe plusieurs points à noter quand vous exécutez les exemples de code dans la documentation [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] :  
  
-   Presque tous les exemples partent du principe que SQL Server 2005 ou version ultérieure (SQL Server 2008 ou version ultérieure si vous utilisez la version 3.1) et la base de données AdventureWorks sont installés sur l’ordinateur local.  
  
    Pour plus d’informations sur la façon de télécharger les éditions gratuites et les versions d’évaluation de SQL Server, consultez [SQL Server](http://go.microsoft.com/fwlink/?LinkID=120193).  
  
    Pour plus d’informations sur le téléchargement de la base de données AdventureWorks, consultez [Exemples et projets de la communauté Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkID=67739).  
  
    Pour plus d’informations sur l’installation de la base de données AdventureWorks, consultez [Procédure pas à pas : installation de la base de données AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=65819).  
  
-   Presque tous les exemples de code de cette documentation sont destinés à être exécutés à partir de la ligne de commande, ce qui permet de les tester tous de manière automatisée. Pour plus d’informations sur l’exécution de PHP à partir de la ligne de commande, consultez [Utilisation de PHP à partir de la ligne de commande](http://php.net/manual/en/features.commandline.php).  
  
-   Bien que les exemples soient écrits pour être exécutés à partir de la ligne de commande, chaque exemple peut être exécuté en étant appelé à partir d’un navigateur sans avoir à apporter des modifications au script. Pour obtenir une mise en forme de sortie lisible, remplacez chaque « \n » par «\<\/br > » dans chaque exemple avant de l’appeler à partir d’un navigateur.  
  
-   Par souci de concision, la gestion des erreurs appropriée n’est pas effectuée dans tous les exemples. Il est recommandé de vérifier s’il existe des erreurs dans tout appel à une fonction **sqlsrv** ou méthode PDO et de les gérer selon les besoins de l’application.  
  
    Un moyen simple d’obtenir des informations d’erreur quand une erreur s’est produite consiste à quitter le script avec la ligne de code suivante :  
  
    ```  
    die( print_r( sqlsrv_errors(), true));  
    ```  
  
    Ou, si vous utilisez PDO,  
  
    ```  
    print_r ($stmt->errorInfo());  
    die();  
    ```  
  
    Pour plus d’informations sur la gestion des erreurs et avertissements, consultez [Gestion des erreurs et des avertissements](../../connect/php/handling-errors-and-warnings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Vue d’ensemble du pilote SQL PHP](../../connect/php/overview-of-the-php-sql-driver.md)
  

