---
title: À propos des exemples de code dans la documentation | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3f035c37-0f2e-47d4-94e0-a10774402e82
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc76cee723c11d49a4d6149a7c3a1df4cedbc256
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015170"
---
# <a name="about-code-examples-in-the-documentation"></a>À propos des exemples de code dans la documentation
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="remarks-about-the-code-examples"></a>Remarques sur les exemples de code
Il existe plusieurs points à noter quand vous exécutez les exemples de code dans la documentation [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] :  
  
-   Presque tous les exemples partent du principe que SQL Server 2008 ou version ultérieure et la base de données AdventureWorks sont installés sur l’ordinateur local.  
  
    Pour plus d’informations sur la façon de télécharger les éditions gratuites et les versions d’évaluation de SQL Server, consultez [SQL Server](https://go.microsoft.com/fwlink/?LinkID=120193).  
  
    Pour plus d’informations sur le téléchargement et l’installation de la base de données AdventureWorks, consultez la [page AdventureWorks dans le référentiel GitHub des exemples SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works).
  
-   Presque tous les exemples de code de cette documentation sont destinés à être exécutés à partir de la ligne de commande, ce qui permet de les tester tous de manière automatisée. Pour plus d’informations sur l’exécution de PHP à partir de la ligne de commande, consultez [Utilisation de PHP à partir de la ligne de commande](https://php.net/manual/en/features.commandline.php).  
  
-   Bien que les exemples soient destinés à être exécutés en ligne de commande, vous pouvez appeler chacun d’entre eux avec un navigateur sans apporter de modifications au script. Pour obtenir une mise en forme de sortie lisible, remplacez chaque « \n » par « \<\/br> » dans chaque exemple avant de l’appeler à partir d’un navigateur.  
  
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
[Vue d’ensemble de Microsoft Drivers for PHP for SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)
  
