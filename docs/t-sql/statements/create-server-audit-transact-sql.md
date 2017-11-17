---
title: CREATE SERVER AUDIT (Transact-SQL) | Documents Microsoft
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
- CREATE_SERVER_AUDIT_TSQL
- SERVER AUDIT
- SERVER_AUDIT_TSQL
- CREATE SERVER AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- CREATE SERVER AUDIT statement
- audits [SQL Server], creating
ms.assetid: 1c321680-562e-41f1-8eb1-e7fa5ae45cc5
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bbeb32f18755a9ecd0bf57f094f0504b60f6eebf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-server-audit-transact-sql"></a>CREATE SERVER AUDIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un objet d'audit de serveur à l'aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit. Pour plus d’informations, consultez [SQL Server Audit &#40moteur de base de données&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE SERVER AUDIT audit_name  
{  
    TO { [ FILE (<file_options> [ , ...n ] ) ] | APPLICATION_LOG | SECURITY_LOG }  
    [ WITH ( <audit_options> [ , ...n ] ) ]   
    [ WHERE <predicate_expression> ]  
}  
[ ; ]  
  
<file_options>::=  
{  
        FILEPATH = 'os_file_path'  
    [ , MAXSIZE = { max_size { MB | GB | TB } | UNLIMITED } ]  
    [ , { MAX_ROLLOVER_FILES = { integer | UNLIMITED } } | { MAX_FILES = integer } ]  
    [ , RESERVE_DISK_SPACE = { ON | OFF } ]   
}  
  
<audit_options>::=  
{  
    [   QUEUE_DELAY = integer ]  
    [ , ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION } ]  
    [ , AUDIT_GUID = uniqueidentifier ]  
}  
  
<predicate_expression>::=  
{  
    [NOT ] <predicate_factor>   
    [ { AND | OR } [NOT ] { <predicate_factor> } ]   
    [,...n ]  
}  
  
<predicate_factor>::=   
    event_field_name { = | < > | ! = | > | > = | < | < = } { number | ' string ' }  
```  
  
## <a name="arguments"></a>Arguments  
 TO { FILE | APPLICATION_LOG | SECURITY_LOG }  
 Détermine l'emplacement de la cible de l'audit. Les options sont un fichier binaire, journal de l’Application Windows ou le journal de sécurité de Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas écrire dans le journal de sécurité Windows sans configurer d'autres paramètres dans Windows. Pour plus d’informations, consultez [Écrire des événements d’audit SQL Server dans le journal de sécurité](../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md).  
  
 Chemin d’accès ='*os_file_path*'  
 Chemin d'accès du journal d'audit. Le nom de fichier est généré en fonction du nom d'audit et du GUID d'audit.  
  
 MAXSIZE = { *max_size}*  
 Taille maximale que peut atteindre le fichier d'audit. Le *max_size* valeur doit être un entier suivi Mo, Go, To ou illimité. La taille minimale que vous pouvez spécifier pour *max_size* est 2 Mo et le maximum est 2 147 483 647 to. Lorsque UNLIMITED est spécifié, la taille du fichier peut croître jusqu'à ce que le disque soit saturé. (0 correspond également à UNLIMITED.) Spécification d’une valeur inférieure à 2 Mo génère l’erreur MSG_MAXSIZE_TOO_SMALL. La valeur par défaut est UNLIMITED.  
  
 MAX_ROLLOVER_FILES =*{entier* | ILLIMITÉ}  
 Spécifie le nombre maximal de fichiers à conserver dans le système de fichiers en plus du fichier actuel. Le *MAX_ROLLOVER_FILES* valeur doit être un entier ou UNLIMITED. La valeur par défaut est UNLIMITED. Ce paramètre est évalué chaque fois que l’audit redémarre (qui peut se produire lorsque l’instance de la [!INCLUDE[ssDE](../../includes/ssde-md.md)] redémarre ou lorsque l’audit est activé, puis à nouveau) ou lorsqu’un nouveau fichier est nécessaire car le paramètre MAXSIZE a été atteint. Lorsque *MAX_ROLLOVER_FILES* est évaluée, si le nombre de fichiers dépasse la *MAX_ROLLOVER_FILES* définition, le fichier le plus ancien est supprimé. Par conséquent, lorsque le paramètre de *MAX_ROLLOVER_FILES* est 0, un nouveau fichier est créé chaque fois que le *MAX_ROLLOVER_FILES* paramètre est évalué. Un seul fichier est automatiquement supprimé quand *MAX_ROLLOVER_FILES* paramètre est évalué, par conséquent, lorsque la valeur de *MAX_ROLLOVER_FILES* est réduite, le nombre de fichiers ne se réduit pas, sauf si les anciens fichiers sont supprimés manuellement. Le nombre maximal de fichiers qui peuvent être spécifiés est 2 147 483 647.  
  
 MAX_FILES =*entier*  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie le nombre maximal de fichiers d'audit qui peuvent être créés. N'effectue pas de substitution vers le premier fichier lorsque la limite est atteinte. Lorsque la limite MAX_FILES est atteinte, toute action qui entraîne la génération, d’événements d’audit supplémentaires échoue avec une erreur.  
  
 RESERVE_DISK_SPACE = { ON | OFF }  
 Cette option pré-alloue la valeur MAXSIZE au fichier sur le disque. Elle s'applique uniquement si MAXSIZE n'est pas égal à UNLIMITED. La valeur par défaut est OFF.  
  
 QUEUE_DELAY =*entier*  
 Détermine la durée, en millisecondes, qui peuvent s’écouler avant que les actions d’audit sont forcées à traiter. Une valeur de 0 indique la remise synchrone. La valeur minimale du délai de requête définissable est 1000 (1 seconde), qui est la valeur par défaut. Le maximum est 2 147 483 647 (2 147 483,647 secondes ou 24 jours, 20 heures, 31 minutes, 23,647 secondes). Spécifiez un nombre non valide, déclenche l’erreur MSG_INVALID_QUEUE_DELAY.  
  
 ON_FAILURE = {CONTINUER | ARRÊT | FAIL_OPERATION}  
 Indique si l'instance qui écrit dans la cible doit échouer, continuer ou arrêter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si la cible ne peut pas écrire dans le journal d'audit. La valeur par défaut est CONTINUE.  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les opérations continuent. Les enregistrements d'audit ne sont pas conservés. L’audit continue de se connecter les événements et reprend si le problème est résolu. En sélectionnant l’option Continuer permet à une activité non auditée susceptible d’enfreindre vos stratégies de sécurité. Utilisez cette option, lors de la poursuite de l’opération de le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est plus importante que la conservation d’un audit complet.  
  
SHUTDOWN  
Force l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l’arrêter, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne parvient pas à écrire des données dans la cible d’audit pour une raison quelconque. La connexion exécutant le `CREATE SERVER AUDIT` instruction doit avoir le `SHUTDOWN` autorisation dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le comportement d’arrêt persiste même si le `SHUTDOWN` autorisation est révoquée ultérieurement à partir de la connexion en cours d’exécution. Si l’utilisateur n’a pas cette autorisation, puis l’instruction échoue et l’audit n'est pas créé. Utilisez cette option si une défaillance de l'audit risque de compromettre la sécurité ou l'intégrité du système. Pour plus d’informations, consultez [arrêt](../../t-sql/language-elements/shutdown-transact-sql.md).  
  
 FAIL_OPERATION  
 Les actions de base de données échouent si elles entraînent des événements audités. Les actions qui n’entraînent pas les événements audités peuvent continuer, mais aucun événement audité ne peut se produire. L’audit continue de se connecter les événements et reprend si le problème est résolu. Utilisez cette option lorsqu'il est plus important de conserver un audit complet que de disposer d'un accès complet au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

 AUDIT_GUID =*uniqueidentifier*  
 Pour prendre en charge des scénarios tels que la mise en miroir de bases de données, un audit a besoin d'un GUID spécifique qui correspond au GUID trouvé dans la base de données mise en miroir. Le GUID ne peut pas être modifié après la création de l'audit.  
  
 predicate_expression  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie l'expression de prédicat utilisée pour déterminer si un événement doit ou non être traité. Les expressions de prédicat sont limitées à 3 000 caractères, ce qui limite les arguments de chaîne.  
  
 event_field_name  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nom du champ d'événement qui identifie la source de prédicat. Les champs d’audit sont décrits dans [sys.fn_get_audit_file &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). Tous les champs peuvent être audités sauf `file_name` et `audit_file_offset`.  
  
 nombre  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Est de n’importe quel type numérique, y compris **décimal**. Le manque de mémoire physique ou un nombre trop grand pour être représenté sous forme d'entier 64 bits sont les seules limitations.  
  
 ' string '  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Chaîne ANSI ou Unicode, comme requis par la comparaison de prédicat. Aucune conversion implicite de type chaîne n'est effectuée pour les fonctions de comparaison de prédicat. La transmission d'un type incorrect provoque une erreur.  
  
## <a name="remarks"></a>Notes  
 Lorsqu'un audit de serveur est créé, il est dans un état désactivé.  
  
 L'instruction CREATE SERVER AUDIT fait partie de l'étendue d'une transaction. Si la transaction est restaurée, l'instruction l'est également.  
  
## <a name="permissions"></a>Permissions  
 Pour créer, modifier ou supprimer un audit du serveur, les principaux requièrent l'autorisation ALTER ANY SERVER AUDIT ou CONTROL SERVER.  
  
 Lorsque vous enregistrez des informations d'audit dans un fichier, pour éviter toute falsification, limitez l'accès à l'emplacement du fichier.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-server-audit-with-a-file-target"></a>A. Création d'un audit du serveur avec une cible de fichier  
 L'exemple suivant crée un audit du serveur nommé `HIPPA_Audit` avec un fichier binaire comme cible et aucune option.  
  
```sql  
CREATE SERVER AUDIT HIPAA_Audit  
    TO FILE ( FILEPATH ='\\SQLPROD_1\Audit\' );  
```  
  
### <a name="b-creating-a-server-audit-with-a-windows-application-log-target-with-options"></a>B. Création d'un audit du serveur avec le journal des applications Windows comme cible et des options  
 L'exemple suivant crée un audit du serveur nommé `HIPPA_Audit` avec la cible définie sur le journal des applications Windows. La file d'attente est écrite chaque seconde et arrête le moteur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cas d'échec.  
  
```sql  
CREATE SERVER AUDIT HIPAA_Audit  
    TO APPLICATION_LOG  
    WITH ( QUEUE_DELAY = 1000,  ON_FAILURE = SHUTDOWN);  
```  
  
###  <a name="ExampleWhere"></a> C. Création d'un audit de serveur contenant une clause WHERE  
 L'exemple suivant crée une base de données, un schéma et deux tables pour l'exemple. La table nommée `DataSchema.SensitiveData` contient des données confidentielles et l’accès à la table doivent être enregistrées dans l’audit. La table `DataSchema.GeneralData` ne contient pas de données confidentielles. La spécification de l'audit de la base de données audite les accès à tous les objets du schéma `DataSchema`. L'audit du serveur est créé avec une clause WHERE qui limite l'audit à la seule table `SensitiveData`. L’audit du serveur suppose un dossier d’audit existe à `C:\SQLAudit`.  
  
```sql  
CREATE DATABASE TestDB;  
GO  
USE TestDB;  
GO  
CREATE SCHEMA DataSchema;  
GO  
CREATE TABLE DataSchema.GeneralData (ID int PRIMARY KEY, DataField varchar(50) NOT NULL);  
GO  
CREATE TABLE DataSchema.SensitiveData (ID int PRIMARY KEY, DataField varchar(50) NOT NULL);  
GO  
-- Create the server audit in the master database  
USE master;  
GO  
CREATE SERVER AUDIT AuditDataAccess  
    TO FILE ( FILEPATH ='C:\SQLAudit\' )  
    WHERE object_name = 'SensitiveData' ;  
GO  
ALTER SERVER AUDIT AuditDataAccess WITH (STATE = ON);  
GO  
-- Create the database audit specification in the TestDB database  
USE TestDB;  
GO  
CREATE DATABASE AUDIT SPECIFICATION [FilterForSensitiveData]  
FOR SERVER AUDIT [AuditDataAccess]   
ADD (SELECT ON SCHEMA::[DataSchema] BY [public])  
WITH (STATE = ON);  
GO  
-- Trigger the audit event by selecting from tables  
SELECT ID, DataField FROM DataSchema.GeneralData;  
SELECT ID, DataField FROM DataSchema.SensitiveData;  
GO  
-- Check the audit for the filtered content  
SELECT * FROM fn_get_audit_file('C:\SQLAudit\AuditDataAccess_*.sqlaudit',default,default);  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CRÉER une spécification d’AUDIT de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys.fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [Sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys.server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [Sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [Sys.server_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [Sys.Database audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [Sys.database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [Sys.dm_server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [Sys.dm_audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Sys.dm_audit_class_type_map &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Créer un audit du serveur et une spécification d’audit du serveur](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  

