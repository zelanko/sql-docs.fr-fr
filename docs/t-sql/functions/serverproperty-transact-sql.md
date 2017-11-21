---
title: SERVERPROPERTY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SERVERPROPERTY_TSQL
- SERVERPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SERVERPROPERTY function
- server instance property information [SQL Server]
- IsHadrEnabled server property
- instances of SQL Server, property information
- server properties [SQL Server]
ms.assetid: 11e166fa-3dd2-42d8-ac4b-04f18c612c4a
caps.latest.revision: 128
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7060a8aaf668a69184503fa0995dd4f37085d5f1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="serverproperty-transact-sql"></a>SERVERPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne des informations de propriété relatives à l'instance du serveur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SERVERPROPERTY ( 'propertyname' )  
```  
  
## <a name="arguments"></a>Arguments  
 *PropertyName*  
 Expression contenant les informations de propriétés à retourner pour le serveur. *PropertyName* peut prendre l’une des valeurs suivantes.  
  
|Propriété|Valeurs retournées|  
|--------------|---------------------|  
|BuildClrVersion|Version de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR) qui a été utilisé lors de la génération de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **nvarchar (128)**|  
|Classement|Nom du classement par défaut pour le serveur.<br /><br /> NULL = Entrée non valide ou erreur.<br /><br /> Type de données de base : **nvarchar (128)**|  
|CollationID|ID du classement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Type de données de base : **int**|  
|ComparisonStyle|Style de comparaison Windows du classement.<br /><br /> Type de données de base : **int**|  
|ComputerNamePhysicalNetBIOS|Nom NetBIOS de l'ordinateur local sur lequel l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d'exécution.<br /><br /> Pour une instance cluster de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un cluster de basculement, cette valeur change étant donné que l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bascule sur d'autres nœuds du cluster de basculement.<br /><br /> Sur une instance autonome de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette valeur reste constante et retourne la même valeur que la propriété MachineName.<br /><br /> **Remarque :** si l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est dans un basculement de cluster et que vous souhaitez obtenir le nom de l’instance de cluster de basculement, utilisez la propriété MachineName.<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **nvarchar (128)**|  
|Édition|Édition du produit installée de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La valeur de cette propriété permet de déterminer les fonctionnalités et les limites, telles que [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md). Les versions 64 bits du [!INCLUDE[ssDE](../../includes/ssde-md.md)] ajoutent la mention (64 bits) à la version.<br /><br /> Retourne les informations suivantes :<br /><br /> « Enterprise Edition »<br /><br /> « Enterprise Edition : contrat de licence selon le nombre de cœurs »<br /><br /> « Enterprise Evaluation Edition »<br /><br /> « Business Intelligence Edition »<br /><br /> « Developer Edition »<br /><br /> « Express Edition »<br /><br /> « Express Edition with Advanced Services »<br /><br /> « Standard Edition »<br /><br /> « Web Edition »<br /><br /> « SQL Azure » indique [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ou[!INCLUDE[ssDW](../../includes/ssdw-md.md)]<br /><br /> Type de données de base : **nvarchar (128)**|  
|EditionID|EditionID représente l'édition de produit installée de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La valeur de cette propriété permet de déterminer les fonctionnalités et limites, tel que [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).<br /><br /> 1804890536 = Enterprise<br /><br /> 1872460670 = Enterprise Edition : contrat de licence selon le nombre de cœurs<br /><br /> 610778273 = Enterprise Evaluation<br /><br /> 284895786 = Business Intelligence<br /><br /> -2117995310 = Developer<br /><br /> -1592396055 = Express<br /><br /> -133711905 = Express with Advanced Services<br /><br /> -1534726760 = standard<br /><br /> 1293598313 = Web<br /><br /> 1674378470 = la base de données SQL ou de l’entrepôt de données SQL<br /><br /> Type de données de base : **bigint**|  
|EngineEdition|Édition du [!INCLUDE[ssDE](../../includes/ssde-md.md)] de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installée sur le serveur.<br /><br /> 1 = Personal ou Desktop Engine (non disponible dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures)<br /><br /> 2 = Standard (valeur retournée pour Standard, Web et Business Intelligence)<br /><br /> 3 = Enterprise (valeur retournée pour les éditions Evaluation, Developer et les deux éditions Enterprise.)<br /><br /> 4 = Express (valeur retournée pour Express, Express with Tools et Express with Advanced Services)<br /><br /> 5 = [!INCLUDE[ssSDS](../../includes/sssds-md.md)]<br /><br /> 6 - [!INCLUDE[ssDW](../../includes/ssdw-md.md)]<br /><br /> Type de données de base : **int**|  
|HadrManagerStatus|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Indique si le gestionnaire [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] a démarré.<br /><br /> 0 = Non démarré, en attente de communication<br /><br /> 1 = Démarré et en cours d'exécution<br /><br /> 2 = Non démarré et en état d'échec<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.|  
|InstanceDefaultDataPath|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à la version actuelle de mises à jour depuis 2015 à liaison tardive.<br /><br /> Nom du chemin d’accès par défaut pour les fichiers de données d’instance.|  
|InstanceDefaultLogPath|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à la version actuelle de mises à jour depuis 2015 à liaison tardive.<br /><br /> Nom du chemin d’accès par défaut pour les fichiers de journaux d’instance.|  
|InstanceName|Nom de l'instance à laquelle l'utilisateur est connecté.<br /><br /> Retourne la valeur NULL si le nom de l'instance est celui de l'instance par défaut, et en cas d'entrée incorrecte ou d'erreur.<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **nvarchar (128)**|  
|IsAdvancedAnalyticsInstalled|Retourne 1 si la fonctionnalité avancée d’Analytique a été installée pendant l’installation ; 0 si Analytique d’avancée n’a pas été installé.|  
|IsClustered|L'instance de serveur est configurée dans un cluster de basculement.<br /><br /> 1 = Ordonné en clusters<br /><br /> 0 = Non cluster<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **int**|  
|IsFullTextInstalled|Les composants d'indexation sémantique et de texte intégral sont installés sur l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = Les composants d'indexation sémantique et de texte intégral sont installés.<br /><br /> 0 = Les composants d'indexation sémantique et de texte intégral ne sont pas installés.<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **int**|  
|IsHadrEnabled|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] est activé sur cette instance de serveur.<br /><br /> 0 = La fonctionnalité [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] est désactivée.<br /><br /> 1 = La fonctionnalité [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] est activée.<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **int**<br /><br /> Pour les réplicas de disponibilité à créer et exécuter sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le service [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] doit être activé sur l'instance de serveur. Pour plus d’informations, consultez [activer et désactiver les groupes de disponibilité AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).<br /><br /> **Remarque :** la propriété IsHadrEnabled se rapporte uniquement au [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]. D'autres fonctionnalités haute disponibilité ou de récupération d'urgence, telles que la mise en miroir de bases de données ou la copie des journaux de transaction, ne sont pas affectées par cette propriété du serveur.|  
|IsIntegratedSecurityOnly|Le serveur fonctionne en mode de sécurité intégrée.<br /><br /> 1 = Sécurité intégrée (authentification Windows)<br /><br /> 0 = Sécurité non intégrée. (Authentification Windows et authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **int**|  
|IsLocalDB|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Le serveur est une instance de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] LocalDB.<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.|  
|IsPolybaseInstalled|**S'applique à**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Retourne si l’instance de serveur possède la fonctionnalité PolyBase est installée.<br /><br /> 0 = PolyBase n’est pas installé.<br /><br /> 1 = PolyBase est installé.<br /><br /> Type de données de base : **int**|  
|IsSingleUser|Le serveur est en mode mono-utilisateur.<br /><br /> 1 = Utilisateur unique<br /><br /> 0 = Utilisateur non unique<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **int**|  
|IsXTPSupported|**S’applique aux**: SQL Server ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> Le serveur prend en charge OLTP en mémoire.<br /><br /> 1 = Le serveur prend en charge OLTP en mémoire.<br /><br /> 0 = Le serveur ne prend pas en charge OLTP en mémoire.<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **int**|  
|LCID|Identificateur des paramètres régionaux (LCID) Windows du classement.<br /><br /> Type de données de base : **int**|  
|LicenseType|Inutilisé. Les informations de licence ne sont pas conservées ou ne sont pas gérées par le produit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Retourne toujours DISABLED.<br /><br /> Type de données de base : **nvarchar (128)**|  
|MachineName|Nom de l'ordinateur Windows sur lequel s'exécute l'instance du serveur.<br /><br /> Dans le cas d'une instance en cluster, instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutant sur un serveur virtuel sous Microsoft Cluster Service, le nom du serveur virtuel est retourné.<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **nvarchar (128)**|  
|NumLicenses|Inutilisé. Les informations de licence ne sont pas conservées ou ne sont pas gérées par le produit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Retourne toujours la valeur Null.<br /><br /> Type de données de base : **int**|  
|ProcessID|ID de processus du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. ProcessID permet d'identifier le fichier sqlservr.exe qui appartient à cette instance.<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.<br /><br /> Type de données de base : **int**|  
|ProductBuild|**S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] depuis octobre 2015.<br /><br /> Le numéro de build.|  
|ProductBuildType|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à la version actuelle de mises à jour depuis 2015 à liaison tardive.<br /><br /> Type de la version de la build actuelle.<br /><br /> Retourne l'une des valeurs suivantes :<br /><br /> OD = mise en production à la demande sur un client spécifique.<br /><br /> GDR = version Distribution générale publiée via windows update.<br /><br /> NULL<br />= Non applicable.|  
|ProductLevel|Niveau de la version de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Retourne l'une des valeurs suivantes :<br /><br /> « 'RTM » = Version d'origine<br /><br /> ' SP*n*' = version du Service pack<br /><br /> « CTP*n*', = version de Community Technology Preview<br /><br /> Type de données de base : **nvarchar (128)**|  
|ProductMajorVersion|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à la version actuelle de mises à jour depuis 2015 à liaison tardive.<br /><br /> La version principale.|  
|ProductMinorVersion|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à la version actuelle de mises à jour depuis 2015 à liaison tardive.<br /><br /> La version mineure.|  
|ProductUpdateLevel|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à la version actuelle de mises à jour depuis 2015 à liaison tardive.<br /><br /> Mettre à jour au niveau de la build en cours. CU indique une mise à jour cumulative.<br /><br /> Retourne l'une des valeurs suivantes :<br /><br /> CU *n*  = mise à jour Cumulative<br /><br /> NULL<br />= Non applicable.|  
|ProductUpdateReference|**S’applique aux**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à la version actuelle de mises à jour depuis 2015 à liaison tardive.<br /><br /> L’article de cette version.|  
|ProductVersion|Version de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sous la forme '*major.minor.build.revision*'.<br /><br /> Type de données de base : **nvarchar (128)**|  
|ResourceLastUpdateDateTime|Retourne la date et l'heure de la dernière mise à jour de la base de données des ressources.<br /><br /> Type de données de base : **datetime**|  
|ResourceVersion|Retourne la base de données des ressources de versions.<br /><br /> Type de données de base : **nvarchar (128)**|  
|ServerName|Informations relatives à l'instance et au serveur Windows, associées à une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NULL = Entrée non valide ou erreur.<br /><br /> Type de données de base : **nvarchar (128)**|  
|SqlCharSet|ID du jeu de caractères SQL provenant de l'ID de classement<br /><br /> Type de données de base : **tinyint**|  
|SqlCharSetName|Nom du jeu de caractères SQL provenant du classement<br /><br /> Type de données de base : **nvarchar (128)**|  
|SqlSortOrder|ID d'ordre de tri SQL provenant du classement<br /><br /> Type de données de base : **tinyint**|  
|SqlSortOrderName|Nom de l'ordre de tri SQL provenant du classement.<br /><br /> Type de données de base : **nvarchar (128)**|  
|FilestreamShareName|Nom du partage utilisé par FILESTREAM.<br /><br /> NULL = Entrée non valide, non applicable, ou erreur.|  
|FilestreamConfiguredLevel|Niveau configuré d'accès de FILESTREAM. Pour plus d’informations, consultez [niveau d’accès filestream](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).|  
|FilestreamEffectiveLevel|Niveau effectif d'accès de FILESTREAM. Cette valeur peut être différente de FilestreamConfiguredLevel si le niveau a changé ou si un redémarrage de l'instance ou de l'ordinateur est en attente. Pour plus d’informations, consultez [niveau d’accès filestream](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).|  
  
## <a name="return-types"></a>Types de retour  
 **sql_variant**  
  
## <a name="remarks"></a>Notes  
  
### <a name="servername-property"></a>Propriété ServerName  
 Le `ServerName` propriété de la `SERVERPROPERTY` (fonction) et [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) retournent des informations similaires. La propriété `ServerName` fournit le serveur et le nom de l'instance Windows qui constituent ensemble l'instance de serveur unique. [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) fournit le nom du serveur local configuré actuellement.  
  
 Le `ServerName` propriété et [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) retournent les mêmes informations si le nom du serveur par défaut au moment de l’installation n’a pas été modifié. Le nom de serveur local peut être configuré en exécutant la commande suivante :  
  
```  
EXEC sp_dropserver 'current_server_name';  
GO  
EXEC sp_addserver 'new_server_name', 'local';  
GO  
```  
  
 Si le nom du serveur local a été modifié à partir du nom de serveur par défaut au moment de l’installation, [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) retourne le nouveau nom.  
  
### <a name="version-properties"></a>Propriétés de version  
 Le `SERVERPROPERTY` fonction retourne les propriétés individuelles qui sont liés aux informations de version, tandis que la [@@VERSION ](../../t-sql/functions/version-transact-sql-configuration-functions.md) fonction combine la sortie dans une chaîne. Si votre application requiert des chaînes de propriété individuelles, vous pouvez utiliser la `SERVERPROPERTY` afin de les retourner au lieu d’analyser le [@@VERSION ](../../t-sql/functions/version-transact-sql-configuration-functions.md) résultats.  

## <a name="permissions"></a>Permissions

Tous les utilisateurs peuvent interroger les propriétés du serveur. 
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise le `SERVERPROPERTY` fonctionner dans un `SELECT` instruction pour retourner des informations sur l’instance actuelle de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].   
  
```  
SELECT  
  SERVERPROPERTY('MachineName') AS ComputerName,
  SERVERPROPERTY('ServerName') AS InstanceName,  
  SERVERPROPERTY('Edition') AS Edition,
  SERVERPROPERTY('ProductVersion') AS ProductVersion,  
  SERVERPROPERTY('ProductLevel') AS ProductLevel;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Éditions et composants de SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)  
  
  

