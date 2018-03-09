---
title: Options de connexion | Documents Microsoft
ms.custom: 
ms.date: 02/08/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d1ea295-8e34-438e-8468-4bbc0f76192c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 899e072051224e2f28423e31f44d368a2884497b
ms.sourcegitcommit: aebbfe029badadfd18c46d5cd6456ea861a4e86d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="connection-options"></a>Options de connexion
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique répertorie les options qui sont autorisées dans le tableau associatif (lors de l’utilisation [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) dans le pilote SQLSRV) ou les mots clés qui sont autorisés dans le nom de source de données (dsn) (lors de l’utilisation [PDO::__construct ](../../connect/php/pdo-construct.md) dans le pilote PDO_SQLSRV).  

|Clé|Valeur| Description|Par défaut|  
|-------|---------|---------------|-----------|  
|APP|Chaîne|Spécifie le nom de l’application utilisé dans le suivi.|Aucune valeur n’est définie.|  
|ApplicationIntent|Chaîne|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont ReadOnly et ReadWrite.<br /><br />Pour plus d’informations sur la prise en charge de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] pour les [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], consultez [Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|ReadWrite|  
|AttachDBFileName|Chaîne|Spécifie le fichier de base de données que le serveur doit attacher.|Aucune valeur n’est définie.|  
|Authentification|Une des chaînes suivantes :<br /><br />'SqlPassword'<br /><br />'ActiveDirectoryPassword'|Spécifie le mode d’authentification.|Pas définie.|  
|CharacterSet<br /><br />(non pris en charge dans le pilote PDO_SQLSRV)|Chaîne|Spécifie le jeu de caractères utilisé pour envoyer des données au serveur.<br /><br />Les valeurs possibles sont SQLSRV_ENC_CHAR et UTF-8. Pour plus d’informations, consultez [How to: Send and Retrieve UTF-8 Data Using Built-In UTF-8 Support](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md).|SQLSRV_ENC_CHAR|  
|ColumnEncryption<br /><br />(uniquement pris en charge dans Windows)|**Activé** ou **désactivé**|Spécifie si la fonctionnalité toujours chiffré est activée ou non. |Désactivé|  
|ConnectionPooling|1 ou **true** pour activer le regroupement de connexions.<br /><br />0 ou **false** pour désactiver le regroupement de connexions.|Spécifie si la connexion est attribuée à partir d’un pool de connexions (1 ou **true**) ou non (0 ou **false**).<sup> 1</sup>|**true** (1)|  
|Base de données|Chaîne|Spécifie le nom de la base de données en cours d’utilisation pour la connexion établie<sup>2</sup>.|Base de données par défaut pour la connexion utilisée.|  
|Pilote|Chaîne|Spécifie le pilote ODBC Microsoft utilisé pour communiquer avec SQL Server.<br /><br />Les valeurs possibles sont :<br />Pilote ODBC 17 pour SQL Server<br />ODBC Driver 13 for SQL Server<br />Pilote ODBC 11 pour SQL Server (Windows uniquement).|Lorsque le mot clé Driver n’est pas spécifié, le Microsoft Drivers for PHP for SQL Server tentent de trouver l’existence des ou les pilotes ODBC Microsoft pris en charge dans le système, en commençant avec la dernière version d’ODBC et ainsi de suite.|  
|Encrypt|1 ou **true** pour activer le chiffrement.<br /><br />0 or **false** pour désactiver le chiffrement.|Spécifie si la communication avec SQL Server est chiffrée (1 ou **true**) ou non (0 ou **false**)<sup>3</sup>.|**false** (0)|  
|Failover_Partner|Chaîne|Spécifie le serveur et l’instance de mise en miroir de la base de données (si elle est activée et configurée) à utiliser quand le serveur principal n’est pas disponible.<br /><br />Il existe des restrictions liées à l’utilisation de Failover_Partner avec MultiSubnetFailover. Pour plus d’informations, consultez [Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|Aucune valeur n’est définie.|  
|LoginTimeout|Entier (pilote SQLSRV)<br /><br />Chaîne (pilote PDO_SQLSRV)|Spécifie le nombre de secondes qui doivent s’écouler avant l’échec de la tentative de connexion.|Aucun délai d’expiration.|  
|MultipleActiveResultSets|1 ou **true** pour utiliser les jeux de résultats actifs multiples.<br /><br />0 ou **false** pour désactiver les jeux de résultats actifs multiples.|Désactive ou active explicitement la prise en charge de MARS (Multiple Active Result Sets).<br /><br />Pour plus d’informations, consultez [Comment : désactiver mars Multiple Active Result &#40; MARS &#41; ](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).|true (1)|  
|MultiSubnetFailover|Chaîne|Toujours spécifier **multiSubnetFailover = yes** lors de la connexion à l’écouteur de groupe de disponibilité d’un [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] groupe de disponibilité ou un [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Instance de Cluster de basculement. **multiSubnetFailover = yes** configure [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] pour fournir une détection plus rapide et la connexion au serveur (actuellement) actif. Les valeurs possibles sont yes et no.<br /><br />Pour plus d’informations sur la prise en charge de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] pour les [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], consultez [Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|non|  
|PWD<br /><br />(non pris en charge dans le pilote PDO_SQLSRV)|Chaîne|Spécifie le mot de passe associé à l’ID d’utilisateur à utiliser lors de la connexion avec l’authentification SQL Server<sup>4</sup>.|Aucune valeur n’est définie.|  
|QuotedId|1 ou **true** pour utiliser les règles SQL-92.<br /><br />0 ou **false** pour utiliser les règles héritées.|Spécifie s’il faut utiliser les règles SQL-92 pour les identificateurs entre guillemets (1 ou **true**) ou pour utiliser les règles Transact-SQL héritées (0 ou **false**).|**true** (1)|  
|ReturnDatesAsStrings<br /><br />(non pris en charge dans le pilote PDO_SQLSRV)|1 ou **true** pour retourner les types de date et d’heure sous forme de chaînes.<br /><br />0 ou **false** pour retourner les types de date et d’heure comme types PHP **DateTime** .|Récupère les types de date et d’heure (datetime, date, time, datetime2 et datetimeoffset) sous forme de chaînes ou en tant que types PHP. Quand vous utilisez le pilote PDO_SQLSRV, les dates sont retournées sous forme de chaînes. Le pilote PDO_SQLSRV n’a pas **datetime** type.<br /><br />Pour plus d’informations, consultez [Procédure : récupérer des types de date et heure sous forme de chaînes à l’aide du pilote SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).|**false**|  
|Défilement|Chaîne|“buffered” indique que vous souhaitez un curseur côté client (mis en mémoire tampon), ce qui vous permet de mettre en cache un jeu de résultats entier en mémoire. Pour plus d’informations, consultez [Types de curseur &#40; Pilote SQLSRV &#41; ](../../connect/php/cursor-types-sqlsrv-driver.md).|Curseur avant uniquement|  
|Server<br /><br />(non pris en charge dans le pilote SQLSRV)|Chaîne|Instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] à laquelle se connecter.<br /><br />Vous pouvez également spécifier un nom de réseau virtuel pour vous connecter à un groupe de disponibilité AlwaysOn. Pour plus d’informations sur la prise en charge de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] pour les [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], consultez [Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|Server est un mot clé obligatoire (mais il ne doit pas obligatoirement être le premier mot clé dans la chaîne de connexion). Si un nom de serveur n’est pas passé au mot clé, une tentative est effectuée pour vous connecter à l’instance locale.<br /><br />La valeur transmise à Server peut être le nom d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou l’adresse IP de l’instance. Vous pouvez éventuellement spécifier un numéro de port (par exemple, `sqlsrv:server=(local),1033`).<br /><br />À compter de la version 3.0 du [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] , vous pouvez aussi spécifier une instance de base de données locale avec `server=(localdb)\instancename`. Pour plus d’informations, consultez [PHP Driver for SQL Server Support for LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).|  
|TraceFile|Chaîne|Spécifie le chemin du fichier utilisé pour les données de trace.|Aucune valeur n’est définie.|  
|TraceOn|1 ou **true** pour activer le traçage.<br /><br />0 ou **false** pour désactiver le traçage.|Spécifie si le traçage ODBC est activé (1 ou **true**) ou désactivé (0 ou **false**) pour la connexion établie.|**false** (0)|  
|TransactionIsolation|Le pilote SQLSRV utilise les valeurs suivantes :<br /><br />SQLSRV_TXN_READ_UNCOMMITTED<br /><br />SQLSRV_TXN_READ_COMMITTED<br /><br />SQLSRV_TXN_REPEATABLE_READ<br /><br />SQLSRV_TXN_SNAPSHOT<br /><br />SQLSRV_TXN_SERIALIZABLE<br /><br />Le pilote PDO_SQLSRV utilise les valeurs suivantes :<br /><br />PDO::SQLSRV_TXN_READ_UNCOMMITTED<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED<br /><br />PDO::SQLSRV_TXN_REPEATABLE_READ<br /><br />PDO::SQLSRV_TXN_SNAPSHOT<br /><br />PDO::SQLSRV_TXN_SERIALIZABLE|Spécifie le niveau d’isolation de la transaction.<br /><br />Pour plus d’informations sur l’isolation des transactions, consultez [SET TRANSACTION ISOLATION LEVEL](http://go.microsoft.com/fwlink/?LinkID=191497) dans la documentation de SQL Server.|SQLSRV_TXN_READ_COMMITTED<br /><br />ou<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED|  
|TransparentNetworkIPResolution|**Activé** ou **désactivé**|Affecte la séquence de connexion lors de la première résolu l’adresse IP du nom d’hôte ne répond pas et qu’il existe plusieurs adresses IP associés avec le nom d’hôte.<br /><br />Il interagit avec MultiSubnetFailover pour fournir des séquences de connexion différents. Pour plus d’informations, consultez [à l’aide de résolution IP de réseau Transparent](https://docs.microsoft.com/en-us/sql/connect/odbc/using-transparent-network-ip-resolution).|Activé|
|TrustServerCertificate|1 ou **true** pour approuver le certificat.<br /><br />0 ou **false** pour ne pas approuver le certificat.|Spécifie si le client doit approuver (1 ou **true**) ou rejeter (0 ou **false**) un certificat de serveur auto-signé.|**false** (0)|  
|UID<br /><br />(non pris en charge dans le pilote PDO_SQLSRV)|Chaîne|Spécifie l’ID d’utilisateur à utiliser lors de la connexion avec l’authentification SQL Server<sup>4</sup>.|Aucune valeur n’est définie.|  
|WSID|Chaîne|Spécifie le nom de l’ordinateur pour le traçage.|Aucune valeur n’est définie.|  

1. Le `ConnectionPooling` attribut ne peut pas être utilisé pour activer ou désactiver le regroupement de connexions dans Linux et Mac. Consultez [regroupement de connexions (Microsoft Drivers for PHP for SQL Server)](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).

2. Toutes les requêtes exécutées sur la connexion établie sont apportées à la base de données spécifiée par la *base de données* attribut. Toutefois, si l’utilisateur dispose des autorisations appropriées, les données dans d’autres bases de données peuvent être accessibles à l’aide d’un nom qualifié complet. Par exemple, si le *master* base de données est définie avec la *base de données* l’attribut de connexion, il est toujours possible d’exécuter une requête Transact-SQL qui accède à la  *AdventureWorks.HumanResources.Employee* table en utilisant le nom qualifié complet.  

3. L’activation de *Encryption* peut avoir un impact sur les performances de certaines applications, en raison de la charge de traitement nécessaire pour chiffrer les données.  

4. Instance de *UID* et *PWD* doivent tous deux être définis lors de la connexion avec l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  

Une grande partie des clés prises en charge sont des attributs de chaîne de connexion ODBC. Pour plus d’informations sur les chaînes de connexion ODBC, consultez [Utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](http://go.microsoft.com/fwlink/?LinkId=105504).  

## <a name="see-also"></a>Voir aussi  
[Connexion au serveur](../../connect/php/connecting-to-the-server.md)  
