---
title: RESTORE REWINDONLY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE_REWINDONLY_TSQL
- RESTORE REWINDONLY
dev_langs:
- TSQL
helpviewer_keywords:
- closing backup devices
- backup devices [SQL Server], rewinding
- media [SQL Server]
- open back devices
- rewinding backup devices
- RESTORE REWINDONLY statement
ms.assetid: 7f825b40-2264-4608-9809-590d0f09d882
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf67d54e58f08296878c0781158e7b878b0b2a49
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="restore-statements---rewindonly-transact-sql"></a>RESTAURER les instructions - REWINDONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rembobine et ferme les périphériques à bandes laissés ouverts par l'instruction BACKUP ou RESTORE exécutée avec l'option NOREWIND. Cette commande n'est prise en charge que dans le cas de périphériques à bandes.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RESTORE REWINDONLY   
FROM <backup_device> [ ,...n ]  
[ WITH {UNLOAD | NOUNLOAD}]  
}   
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | TAPE = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}   
```  
  
## <a name="arguments"></a>Arguments  
 **\<backup_device> ::=** 
  
 Spécifie les unités de sauvegarde logiques ou physiques à utiliser pour l'opération de restauration.  
  
 { *logical_backup_device_name* | **@*** logical_backup_device_name_var* } est le nom logique, qui doit respecter les règles des identificateurs, les unités de sauvegarde créé par **sp_addumpdevice** à partir de laquelle la base de données est restaurée. Fourni comme variable (**@***logical_backup_device_name_var*), le nom de l’unité de sauvegarde peut être spécifié comme constante de chaîne (**@*** logical_backup_device_name_var*  =   *logical_backup_device_name*) ou comme une variable de type chaîne de caractères, à l’exception de la **ntext** ou **texte** des types de données.  
  
 {DISQUE | BANDE}  **=**  { **'***nom_unité_sauvegarde_physique***'** | **@*** physical_backup_device_name_var*  } Permet aux sauvegardes d’être restauré à partir de l’unité de disque ou bande nommée. Les types d’appareils de disk et tape doivent être spécifiés avec le nom réel (par exemple, chemin d’accès et nom complet) de l’appareil : disque = 'C:\Program Files\Microsoft SQL Server\MSSQL\BACKUP\Mybackup.bak' ou TAPE = '\\\\. \TAPE0'. S’il est spécifié en tant que variable (**@***physical_backup_device_name_var*), le nom du périphérique peut être spécifié comme constante de chaîne (**@*** physical_backup_device_name_var* = '* physcial_backup_device_name *') ou comme une variable de type chaîne de caractères, à l’exception de la **ntext** ou **texte** des types de données.  
  
 Si vous utilisez un serveur réseau pourvu d'un nom UNC (qui doit contenir le nom de l'ordinateur), spécifiez le type d'unité DISK. Pour plus d’informations sur l’utilisation des noms UNC, consultez [unités de sauvegarde &#40; SQL Server &#41; ](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
 Le compte sous lequel vous exécutez Microsoft SQL Server doit avoir accès en lecture à l’ordinateur distant ou un serveur réseau afin d’effectuer une opération de restauration.  
  
 *n*  
 Espace réservé qui permet de spécifier plusieurs unités de sauvegarde et des unités de sauvegarde logiques. Le nombre maximal d’unités de sauvegarde ou d’unités logiques de sauvegarde est **64**.  
  
 Le nombre d'unités de sauvegarde nécessaires varie si la restauration est hors ligne ou en ligne et devra peut-être correspondre au nombre utilisé pour créer le support de sauvegarde auquel les sauvegardes appartiennent. La restauration hors ligne permet de restaurer une sauvegarde en utilisant moins d'unités que le nombre nécessaire pour créer la sauvegarde. La restauration en ligne nécessite toutes les unités de sauvegarde. Toute tentative avec un nombre d'unités inférieur échoue.  
  
 Pour plus d’informations, consultez [Unités de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md).  
  
> [!NOTE]  
>  Si vous restaurez une sauvegarde à partir d'un support de sauvegarde miroir, vous ne pouvez spécifier qu'un seul miroir pour chaque famille de supports. Néanmoins, en cas d'erreurs, les autres miroirs permettent de résoudre certains problèmes liés à la restauration rapidement. Vous pouvez remplacer un volume de supports endommagé par le volume correspondant d'un autre miroir. En ce qui concerne les restaurations hors ligne, vous pouvez restaurer un nombre de supports inférieur au nombre de familles de supports, mais chaque famille n'est traitée qu'une seule fois.  
  
 **AVEC les Options**  
  
 UNLOAD  
 Indique que la bande est automatiquement rembobinée et démontée lorsque la restauration est terminée. UNLOAD est définie par défaut lorsqu'une nouvelle session utilisateur démarre. Elle reste valide jusqu'à ce que NOUNLOAD soit spécifiée. Cette option n'est utilisée que dans le cas d'unités de bande. Si une unité autre qu'un lecteur de bandes est utilisée pour la restauration, cette option est ignorée.  
  
 NOUNLOAD  
 Indique que la bande ne sera pas démontée automatiquement du lecteur de bande après une restauration. NOUNLOAD reste valide jusqu'à ce que UNLOAD soit spécifiée.  
  
 Indique que la bande ne sera pas démontée automatiquement du lecteur de bande après une restauration. NOUNLOAD reste valide jusqu'à ce que UNLOAD soit spécifiée.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 RESTORE REWINDONLY est une alternative à RESTORE LABELONLY FROM TAPE = \<nom > WITH REWIND. Vous pouvez obtenir la liste des lecteurs de bande ouvert à partir de la [sys.dm_io_backup_tapes](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) vue de gestion dynamique.  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Tout utilisateur peut utiliser RESTORE REWINDONLY.  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Historique de sauvegarde et informations d’en-tête &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

