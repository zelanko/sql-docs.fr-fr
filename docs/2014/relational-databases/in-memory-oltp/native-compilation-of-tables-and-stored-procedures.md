---
title: Compilation en mode natif de tables et de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5880fbd9-a23e-464a-8b44-09750eeb2dad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e70ab55fedcc5053cf82a78c040c850a23824eb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63075192"
---
# <a name="native-compilation-of-tables-and-stored-procedures"></a>Compilation en mode natif de tables et de procédures stockées
  L'OLTP en mémoire introduit le concept de compilation native. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut compiler en mode natif des procédures stockées qui accèdent aux tables optimisées en mémoire. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut également compiler en mode natif des tables optimisées en mémoire. La compilation native permet un accès aux données plus rapide et une exécution des requêtes plus efficace que le [!INCLUDE[tsql](../../includes/tsql-md.md)](traditionnel) interprété. La compilation en mode natif de tables et de procédures stockées produit des DLL.  
  
 La compilation en mode natif des types de table optimisée en mémoire est également prise en charge. Pour plus d'informations, consultez [Memory-Optimized Table Variables](../../database-engine/memory-optimized-table-variables.md).  
  
 La compilation native fait référence au processus de conversion des constructions de programmation en code natif, constitué d'instructions de processeur, sans recourir à une compilation ou une interprétation supplémentaire.  
  
 L'OLTP en mémoire compile les tables optimisées en mémoire quand elles sont créées, ainsi que les procédures stockées compilées en mode natif au moment de leur chargement dans des DLL natives. En outre, les DLL sont recompilées au redémarrage de la base de données ou du serveur. Les informations nécessaires pour recréer les DLL sont stockées dans les métadonnées de la base de données. Les DLL ne font pas partie de la base de données, bien qu'elles lui soient associées. Par exemple, les DLL ne sont pas incluses dans les sauvegardes de base de données.  
  
> [!NOTE]  
>  Les tables optimisées en mémoire sont recompilées lors d'un redémarrage du serveur. Pour accélérer la récupération de la base de données, les procédures stockées compilées en mode natif ne sont pas recompilées lors d'un redémarrage du serveur. Elles sont compilées au moment de la première exécution. En conséquence de cette compilation différée, les procédures stockées compilées en mode natif n’apparaissent que lors de l’appel de [sys.dm_os_loaded_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql) après la première exécution.  
  
## <a name="maintenance-of-in-memory-oltp-dlls"></a>Maintenance des DLL de l'OLTP en mémoire  
 La requête suivante affiche toutes les DLL de tables et de procédures stockées ayant été chargées en mémoire sur le serveur :  
  
```sql  
SELECT name, description FROM sys.dm_os_loaded_modules  
where description = 'XTP Native DLL'  
```  
  
 Les administrateurs de base de données n'ont pas besoin de conserver les fichiers générés par la compilation native. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprime automatiquement les fichiers générés qui ne sont plus nécessaires. Par exemple, les fichiers générés sont supprimés lorsque vous supprimez une table et une procédure stockée, ou si vous supprimez une base de données.  
  
> [!NOTE]  
>  Si la compilation échoue ou est interrompue, certains fichiers générés ne sont pas supprimés. Ces fichiers sont intentionnellement conservés pour la prise en charge et sont supprimés lorsque la base de données est supprimée.  
  
> [!NOTE]  
>  Lors du démarrage de la base de données, SQL Server compile les DLL de toutes les tables nécessaires à la récupération de la base de données. Si une table a été supprimée juste avant un redémarrage de la base de données, il peut y avoir des restes de la table dans les fichiers de point de contrôle ou dans le journal des transactions : la DLL de la table doit alors être recompilée lors du démarrage de la base de données. Après le redémarrage, la DLL est déchargée et les fichiers supprimés par le processus de nettoyage normal.  
  
## <a name="native-compilation-of-tables"></a>Compilation native des tables  
 La création d'une table optimisée en mémoire à l'aide de l'instruction `CREATE TABLE` entraîne l'écriture des informations de la table dans les métadonnées de la base de données et la création des structures de table et d'index en mémoire. La table sera également compilée dans une DLL.  
  
 Consultez l'exemple de script suivant, qui crée une base de données et une table optimisée en mémoire :  
  
```sql  
use master  
go  
create database db1  
go  
alter database db1 add filegroup db1_mod contains memory_optimized_data  
go  
-- adapt filename as needed  
alter database db1 add file (name='db1_mod', filename='c:\data\db1_mod') to filegroup db1_mod  
go  
use db1  
go  
create table dbo.t1  
   (c1 int not null primary key nonclustered,  
    c2 INT)  
with (memory_optimized=on)  
go  
-- retrieve the path of the DLL for table t1  
select name, description FROM sys.dm_os_loaded_modules  
where name like '%xtp_t_' + cast(db_id() as varchar(10)) + '_' + cast(object_id('dbo.t1') as varchar(10)) + '.dll'  
go  
```  
  
 La création de la table crée également la DLL de table et charge la DLL dans la mémoire. Une requête DMV exécutée immédiatement après l'instruction CREATE TABLE récupère le chemin d'accès de la DLL de table.  
  
 La DLL de table comprend les structures d'index et le format de ligne de la table. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise la DLL pour parcourir les index, extraire des lignes et enregistrer le contenu des lignes.  
  
## <a name="native-compilation-of-stored-procedures"></a>Procédures stockées compilées en mode natif  
 Les procédures stockées qui sont identifiées par NATIVE_COMPILATION sont compilées en mode natif. Cela signifie que toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] de la procédure sont compilées en code natif en vue d'accélérer l'exécution de la logique métier critique pour les performances.  
  
 Pour plus d'informations sur les procédures stockées compilées en mode natif, consultez [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).  
  
 Prenons l'exemple de procédure stockée suivant, qui insère des lignes dans la table t1 de l'exemple précédent :  
  
```sql  
create procedure dbo.native_sp  
with native_compilation, schemabinding, execute as owner  
as  
begin atomic  
with (transaction isolation level=snapshot, language=N'us_english')  
  
  declare @i int = 1000000  
  while @i > 0  
  begin  
    insert dbo.t1 values (@i, @i+1)  
    set @i -= 1  
  end  
  
end  
go  
exec dbo.native_sp  
go  
-- reset  
delete from dbo.t1  
go  
```  
  
 La DLL de native_sp peut interagir directement avec la DLL de t1, ainsi que le moteur de stockage de l'OLTP en mémoire, pour insérer les lignes le plus rapidement possible.  
  
 Le compilateur de l'OLTP en mémoire tire parti de l'optimiseur de requête pour créer un plan d'exécution efficace pour chacune des requêtes dans la procédure stockée. Notez que les procédures stockées compilées en mode natif ne sont pas automatiquement recompilées si les données de la table sont modifiées. Pour plus d’informations sur la gestion des statistiques et des procédures stockées avec l’OLTP en mémoire, consultez [Statistiques pour les tables mémoire optimisées](memory-optimized-tables.md).  
  
## <a name="security-considerations-for-native-compilation"></a>Considérations sur la sécurité à prendre en compte pour une compilation native  
 La compilation native des tables et des procédures stockées utilise le compilateur de l'OLTP en mémoire. Ce compilateur génère des fichiers qui sont écrits sur le disque et chargés en mémoire. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise les mécanismes suivants pour restreindre l'accès à ces fichiers.  
  
### <a name="native-compiler"></a>Compilateur natif  
 Le fichier exécutable du compilateur, ainsi que les fichiers binaires et les fichiers d'en-tête nécessaires pour la compilation native, sont installés dans le cadre de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le dossier MSSQL\Binn\Xtp. Par conséquent, si l’instance par défaut est installée sous c:\Program Files, les fichiers du compilateur sont installés\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans c:\Program Files \MSSQL12. MSSQLSERVER\MSSQL\Binn\Xtp.  
  
 Pour limiter l'accès au compilateur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des listes de contrôle d'accès (ACL) qui permettent de restreindre l'accès aux fichiers binaires. Tous les fichiers binaires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont protégés contre la modification ou la falsification via des listes de contrôle d'accès. Les listes de contrôle d'accès du compilateur natif limitent également l'utilisation du compilateur ; seuls le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les administrateurs système disposent des autorisations de lecture et d'exécution des fichiers du compilateur natif.  
  
### <a name="files-generated-by-a-native-compilation"></a>Fichiers générés par une compilation native  
 Les fichiers créés lorsqu'une table ou une procédure stockée est compilée sont les fichiers DLL et les fichiers intermédiaires, notamment les fichiers portant les extensions suivantes : .c, .obj, .xml et .pdb. Les fichiers générés sont enregistrés dans un sous-dossier du dossier de données par défaut. Le sous-dossier est appelé Xtp. Lors de l’installation de l’instance par défaut avec le dossier de données par défaut, les fichiers\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]générés sont placés dans C:\Program Files \MSSQL12. MSSQLSERVER\MSSQL\DATA\Xtp.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] empêche la falsification avec les DLL générées de trois manières :  
  
-   Lorsqu'une table ou une procédure stockée est compilée dans une DLL, cette DLL est immédiatement chargée en mémoire et liée au processus sqlserver.exe. Un fichier DLL ne peut pas être modifié lorsqu'il est lié à un processus.  
  
-   Lorsqu'une base de données redémarre, toutes les tables et les procédures stockées sont recompilées (supprimées et recréés) en fonction des métadonnées de la base de données. Ceci entraîne la suppression des éventuelles modifications apportées à un fichier généré par un agent malveillant.  
  
-   Les fichiers générés sont considérés comme faisant partie des données utilisateur, et ont les mêmes restrictions de sécurité, via les listes de contrôle d'accès, que les fichiers de base de données : seuls le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les administrateurs système ont accès à ces fichiers.  
  
 Aucune intervention de l'utilisateur n'est nécessaire pour gérer ces fichiers. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée et supprime les fichiers, le cas échéant.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables optimisées en mémoire](memory-optimized-tables.md)   
 [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)  
  
  
