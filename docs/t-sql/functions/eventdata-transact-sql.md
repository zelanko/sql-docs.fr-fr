---
title: EVENTDATA (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EVENTDATA
- fn_event_data
- EVENTDATA_TSQL
- fn_event_data_TSQL
dev_langs: TSQL
helpviewer_keywords:
- server instance event data [SQL Server]
- event notifications [SQL Server], event status
- events [SQL Server], status infromation
- EVENTDATA function
- status information [SQL Server], events
- DDL triggers, returning event data
ms.assetid: 03a80e63-6f37-4b49-bf13-dc35cfe46c44
caps.latest.revision: "55"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 45f9d434e5833180320dcb3184fdcceec56c715c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="eventdata-transact-sql"></a>EVENTDATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les événements de serveur et de base de données. EVENTDATA est appelé lorsqu'une notification d'événement est déclenchée, et les résultats sont retournés au service broker spécifié. EVENTDATA peut également être utilisé dans le corps d'un déclencheur DDL ou de connexion.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EVENTDATA( )  
```  
  
## <a name="remarks"></a>Notes  
 La fonction EVENTDATA renvoie des données uniquement si elle est référencée directement au sein d'un déclencheur DDL ou de connexion. Cette fonction retourne la valeur NULL si elle est appelée par d'autres routines, même si ces routines sont appelées par un déclencheur DDL ou d'ouverture de session.  
  
 Les données retournées par EVENTDATA ne sont pas valides après qu'une transaction qui a appelé EVENTDATA, implicitement ou explicitement, est validée ou restaurée.  
  
> [!CAUTION]  
>  EVENTDATA retourne des données XML. Ces données sont envoyées au client sous la forme d'Unicode qui utilise 2 octets pour chaque caractère. Les points de code Unicode suivants peuvent être représentés dans le XML qui est retourné par EVENTDATA :  
>   
>  `0x0009`  
>   
>  `0x000A`  
>   
>  `0x000D`  
>   
>  `>= 0x0020 && <= 0xD7FF`  
>   
>  `>= 0xE000 && <= 0xFFFD`  
>   
>  Certains caractères susceptibles d'apparaître dans des identificateurs et des données [!INCLUDE[tsql](../../includes/tsql-md.md)] ne peuvent pas être exprimés ou autorisés en XML. Les caractères ou données ayant des points de code non représentés dans la liste précédente sont mappés sur un point d'interrogation (?).  
  
 Pour protéger la sécurité des connexions, les mots de passe ne sont pas affichés lors de l'exécution des instructions CREATE LOGIN ou ALTER LOGIN.  
  
## <a name="schemas-returned"></a>Schémas retournés  
 EVENTDATA retourne une valeur de type **xml**. Par défaut, la définition de schéma pour tous les événements est installée dans le répertoire suivant : [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events .xsd.  
  
 Vous pouvez également le schéma d’événement est publié à le [Microsoft SQL Server XML Schemas](http://go.microsoft.com/fwlink/?LinkID=31850) page Web.  
  
 Pour extraire le schéma pour un événement particulier, recherchez dans le schéma le type complexe `EVENT_INSTANCE_\<event_type>`. Par exemple, pour extraire le schéma pour l'événement DROP_TABLE, recherchez dans le schéma `EVENT_INSTANCE_DROP_TABLE`.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-querying-event-data-in-a-ddl-trigger"></a>A. Interrogation des données d'événement dans un déclencheur DDL  
 Cet exemple crée un déclencheur DDL pour empêcher la création de nouvelles tables dans la base de données. L'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] qui active le déclencheur est capturée à utilisant XQuery sur les données XML qui sont générées par EVENTDATA. Pour plus d’informations, consultez [Informations de référence sur le langage XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md).  
  
> [!NOTE]  
>  Lorsque vous interrogez le `\<TSQLCommand>` élément à l’aide de **résultats dans des grilles** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], sauts de ligne dans le texte de commande n’apparaissent pas. Utilisez **résultats dans du texte** à la place.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER safety   
ON DATABASE   
FOR CREATE_TABLE   
AS   
    PRINT 'CREATE TABLE Issued.'  
    SELECT EVENTDATA().value  
        ('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
   RAISERROR ('New tables cannot be created in this database.', 16, 1)   
   ROLLBACK  
;  
GO  
--Test the trigger.  
CREATE TABLE NewTable (Column1 int);  
GO  
--Drop the trigger.  
DROP TRIGGER safety  
ON DATABASE;  
GO  
```  
  
> [!NOTE]  
>  Lorsque vous souhaitez retourner les données d’événement, nous vous recommandons d’utiliser la fonction XQuery **value()** méthode au lieu du **query()** (méthode). Le **query()** méthode retourne XML et transport de séquence d’échappement perluète et instances (CR/LF) de saut de ligne dans la sortie, tandis que la **value()** méthode restitue des instances CR/LF invisibles à la sortie.  
  
### <a name="b-creating-a-log-table-with-event-data-in-a-ddl-trigger"></a>B. Création d'une table de journal avec données d'événements dans un déclencheur DDL  
 Cet exemple crée une table pour stocker des informations sur tous les événements de niveau base de données, et remplit la table avec un déclencheur DDL. Le type d'événement et l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] sont capturés en utilisant XQuery sur les données XML générées par `EVENTDATA`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE ddl_log (PostTime datetime, DB_User nvarchar(100), Event nvarchar(100), TSQL nvarchar(2000));  
GO  
CREATE TRIGGER log   
ON DATABASE   
FOR DDL_DATABASE_LEVEL_EVENTS   
AS  
DECLARE @data XML  
SET @data = EVENTDATA()  
INSERT ddl_log   
   (PostTime, DB_User, Event, TSQL)   
   VALUES   
   (GETDATE(),   
   CONVERT(nvarchar(100), CURRENT_USER),   
   @data.value('(/EVENT_INSTANCE/EventType)[1]', 'nvarchar(100)'),   
   @data.value('(/EVENT_INSTANCE/TSQLCommand)[1]', 'nvarchar(2000)') ) ;  
GO  
--Test the trigger.  
CREATE TABLE TestTable (a int);  
DROP TABLE TestTable ;  
GO  
SELECT * FROM ddl_log ;  
GO  
--Drop the trigger.  
DROP TRIGGER log  
ON DATABASE;  
GO  
--Drop table ddl_log.  
DROP TABLE ddl_log;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisez la fonction EVENTDATA](../../relational-databases/triggers/use-the-eventdata-function.md)   
 [Déclencheurs DDL](../../relational-databases/triggers/ddl-triggers.md)   
 [Notifications d'événements](../../relational-databases/service-broker/event-notifications.md)   
 [Déclencheurs de connexion](../../relational-databases/triggers/logon-triggers.md)  
  
  
