---
title: "Journalisation de l’activité | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logging activity
ms.assetid: a777b3d9-2262-4e82-bc82-b62ad60d0e55
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d748bac061fdd4b76b1df0b9a6cf0a8101f21092
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="logging-activity"></a>Journalisation de l’activité
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Par défaut, les erreurs et avertissements générés par le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] ne sont pas enregistrés. Cette rubrique explique comment configurer la journalisation de l’activité.  
  
## <a name="logging-activity-using-the-pdosqlsrv-driver"></a>Journalisation de l’activité à l’aide du pilote PDO_SQLSRV  
La seule configuration disponible pour le pilote PDO_SQLSRV est l’entrée pdo_sqlsrv.log_severity dans le fichier php.ini.  
  
Ajoutez ce qui suit à la fin de votre fichier php.ini :  
  
```  
[pdo_sqlsrv]  
pdo_sqlsrv.log_severity = <number>  
```  
  
**log_severity** peut avoir l’une des valeurs suivantes :  
  
|Valeur|Description|  
|---------|---------------|  
|0|La journalisation est désactivée (valeur par défaut si rien n’est défini).|  
|-1|Spécifie que les erreurs, avertissements et avis doivent être enregistrés.|  
|1|Spécifie que les erreurs doivent être enregistrées.|  
|2|Spécifie que les avertissements doivent être enregistrés.|  
|4|Spécifie que les avis doivent être enregistrés.|  
  
Les informations de journalisation seront ajoutées au fichier phperrors.log.  
  
PHP lit le fichier de configuration lors de l’initialisation et stocke les données dans une mémoire cache. Il fournit aussi une API pour mettre à jour ces paramètres et les utiliser immédiatement, et est écrit dans le fichier de configuration. Cette API permet aux scripts d’application de modifier les paramètres même après l’initialisation de PHP.  
  
## <a name="logging-activity-using-the-sqlsrv-driver"></a>Journalisation de l’activité à l’aide du pilote SQLSRV  
Pour activer la journalisation, vous pouvez utiliser la fonction [sqlsrv_configure](../../connect/php/sqlsrv-configure.md) ou modifier le fichier php.ini. Vous pouvez enregistrer l’activité en cas d’initialisation, de connexion, d’exécution d’instruction ou de fonction d’erreur. Vous pouvez également spécifier s’il faut enregistrer les erreurs, les avertissements, les avis ou les trois.  
  
> [!NOTE]  
> Vous pouvez configurer l’emplacement du fichier journal dans le fichier php.ini.  
  
### <a name="turning-logging-on"></a>Activation de la journalisation  
Vous pouvez activer la journalisation à l’aide de la fonction [sqlsrv_configure](../../connect/php/sqlsrv-configure.md) pour spécifier une valeur pour le paramètre **LogSubsystems** . Par exemple, la ligne de code suivante configure le pilote pour enregistrer l’activité des connexions :  
  
`sqlsrv_configure("LogSubsystems", SQLSRV_LOG_SYSTEM_CONN);`  
  
Le tableau suivant décrit les constantes que vous pouvez utiliser comme valeur du paramètre **LogSubsystems** :  
  
|Valeur (entier équivalent entre parenthèses)| Description|  
|-----------------------------------------------|---------------|  
|SQLSRV_LOG_SYSTEM_ALL (-1)|Active la journalisation de tous les sous-systèmes.|  
|SQLSRV_LOG_SYSTEM_OFF (0)|Désactive la journalisation. Il s'agit du paramètre par défaut.|  
|SQLSRV_LOG_SYSTEM_INIT (1)|Active la journalisation de l’activité d’initialisation.|  
|SQLSRV_LOG_SYSTEM_CONN (2)|Active la journalisation de l’activité de connexion.|  
|SQLSRV_LOG_SYSTEM_STMT (4)|Active la journalisation de l’activité d’instruction.|  
|SQLSRV_LOG_SYSTEM_UTIL (8)|Active la journalisation de l’activité de fonctions d’erreur (telle que handle_error et handle_warning).|  
  
Vous pouvez définir plusieurs valeurs à la fois pour le **LogSubsystems** à l’aide de l’opérateur logique OR (|). Par exemple, la ligne de code suivante active la journalisation de l’activité pour les connexions et les instructions :  
  
`sqlsrv_configure("LogSubsystems", SQLSRV_LOG_SYSTEM_CONN | SQLSRV_LOG_SYSTEM_STMT);`  
  
Vous pouvez également activer la journalisation en spécifiant une valeur entière pour le paramètre **LogSubsystems** dans le fichier php.ini. Par exemple, ajoutez la ligne suivante à la section `[sqlsrv]` du fichier php.ini pour activer la journalisation de l’activité de connexion :  
  
`sqlsrv.LogSubsystems = 2`  
  
En ajoutant des valeurs entières, vous pouvez spécifier plusieurs options à la fois. Par exemple, ajoutez la ligne suivante à la section `[sqlsrv]` du fichier php.ini pour activer la journalisation de l’activité de connexion et d’instruction :  
  
`sqlsrv.LogSubsystems = 6`  
  
### <a name="logging-errors-warnings-and-notices"></a>Journalisation des erreurs, avertissements et avis  
Après avoir activé la journalisation, vous devez spécifier les éléments à enregistrer. Vous pouvez enregistrer un ou plusieurs des éléments suivants : erreurs, avertissements et avis. Par exemple, la ligne de code suivante spécifie que seuls les avertissements doivent être enregistrés :  
  
`sqlsrv_configure("LogSeverity", SQLSRV_LOG_SEVERITY_WARNING);`  
  
> [!NOTE]  
> La valeur par défaut **LogSeverity** est **SQLSRV_LOG_SEVERITY_ERROR**. Si la journalisation est activée et qu’aucun paramètre pour **LogSeverity** n’a été spécifié, seules les erreurs sont enregistrées.  
  
Le tableau suivant décrit les constantes que vous pouvez utiliser comme valeur du paramètre **LogSeverity** :  
  
|Valeur (entier équivalent entre parenthèses)| Description|  
|-----------------------------------------------|---------------|  
|SQLSRV_LOG_SEVERITY_ALL (-1)|Spécifie que les erreurs, avertissements et avis doivent être enregistrés.|  
|SQLSRV_LOG_SEVERITY_ERROR (1)|Spécifie que les erreurs doivent être enregistrées. Il s'agit du paramètre par défaut.|  
|SQLSRV_LOG_SEVERITY_WARNING (2)|Spécifie que les avertissements doivent être enregistrés.|  
|SQLSRV_LOG_SEVERITY_NOTICE (4)|Spécifie que les avis doivent être enregistrés.|  
  
Vous pouvez définir plusieurs valeurs à la fois pour le **LogSeverity** à l’aide de l’opérateur logique OR (|). Par exemple, la ligne de code suivante spécifie que les erreurs et les avertissements doivent être enregistrés :  
  
`sqlsrv_configure("LogSeverity", SQLSRV_LOG_SEVERITY_ERROR | SQLSRV_LOG_SEVERITY_WARNING);`  
  
> [!NOTE]  
> Le fait de spécifier une valeur pour le paramètre **LogSeverity** n’active pas la journalisation. Vous devez activer la journalisation en spécifiant une valeur pour le paramètre **LogSubsystems** , puis spécifier la gravité des éléments enregistrés en affectant une valeur à **LogSeverity**.  
  
Vous pouvez également affecter une valeur au paramètre **LogSeverity** en spécifiant des valeurs entières dans le fichier php.ini. Par exemple, ajoutez la ligne suivante à la section `[sqlsrv]` du fichier php.ini pour activer uniquement la journalisation des avertissements :  
  
`sqlsrv.LogSeverity = 2`  
  
En ajoutant des valeurs entières, vous pouvez spécifier plusieurs options à la fois. Par exemple, ajoutez la ligne suivante à la section `[sqlsrv]` du fichier php.ini pour activer la journalisation des erreurs et des avertissements :  
  
`sqlsrv.LogSeverity = 3`  
  
## <a name="see-also"></a>Voir aussi  
[Guide de programmation pour le pilote SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[constantes &#40; Microsoft Drivers for PHP for SQL Server &#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  
[sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md)  
[référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  

