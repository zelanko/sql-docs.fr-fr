---
title: Modification des tables à mémoire optimisée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d1ae35d9dae03292edf31cd2b06acf97dc0db0c
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783238"
---
# <a name="altering-memory-optimized-tables"></a>Modification des tables à mémoire optimisée
  L'exécution d'opérations ALTER sur les tables mémoire optimisées n'est pas prise en charge. Cela comprend les opérations telles que la modification du nombre de compartiments, l'ajout ou la suppression d'un index et l'ajout ou la suppression d'une colonne. Cette rubrique fournit des instructions pour mettre à jour des tables mémoire optimisées.  
  
## <a name="updating-the-definition-of-a-memory-optimized-table"></a>Mise à jour de la définition d'une table mémoire optimisée  
 Pour mettre à jour la définition d'une table mémoire optimisée, vous devez créer une nouvelle table avec la définition de la table mise à jour, copiez les données dans la nouvelle table et commencer à utiliser la nouvelle table. Sauf si la table est en lecture seule, vous devez arrêter la charge de travail sur la table, afin de garantir qu'aucune modification n'est apportée à la table pendant la copie des données.  
  
 La procédure suivante présente les étapes nécessaires pour mettre à jour une table. Dans cet exemple, la mise à jour ajoute un index. Cette procédure conserve le nom de la table et nécessite deux opérations de copie de données : une dans une table temporaire et une dans la nouvelle table. La modification du nombre de compartiments (bucket_count) d'un index ou l'ajout ou la suppression d'une colonne s'effectuent de la même façon.  
  
1.  Arrêtez la charge de travail sur la table.  
  
2.  Générez un script pour la table et ajoutez le nouvel index au script.  
  
3.  Générez un script pour les objets liés au schéma (principalement des procédures stockées compilées en mode natif) référençant la table T et leurs autorisations.  
  
     Vous trouverez les objets liés au schéma référençant la table à l'aide de la requête suivante :  
  
    ```sql  
    declare @t nvarchar(255) = N'<table name>'  
  
    select r.referencing_schema_name, r.referencing_entity_name  
    from sys.dm_sql_referencing_entities (@t, 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
    where r.is_caller_dependent = 0 and m.is_schema_bound=1;  
    ```  
  
     Les autorisations d'une procédure stockée peuvent faire l'objet d'un script à l'aide du code [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant :  
  
    ```sql  
    declare @sp nvarchar(255) = N'<procedure name>'  
    declare @permissions nvarchar(max) = N''  
  
    select @permissions += dp.state_desc + N' ' + dp.permission_name + N' ON ' +   
       quotename(schema_name(o.schema_id)) + N'.' + quotename(o.name) + N' TO ' +  
       quotename(u.name) + N'; ' + char(13)  
    from sys.database_permissions as dp  
  
    join sys.database_principals as u  
       on u.principal_id = dp.grantee_principal_id  
  
    join sys.objects as o  
       on o.object_id = dp.major_id  
    where dp.class = 1 /* object */  
       and dp.minor_id = 0 and o.object_id=object_id(@sp);  
  
    select @permissions  
    ```  
  
4.  Créez une copie de la table et copiez les données de la table d'origine dans la copie de la table. La copie peut être créée à l’aide des [!INCLUDE[tsql](../../includes/tsql-md.md)]<sup>1</sup>ci-dessous.  
  
    ```sql  
    select * into dbo.T_copy from dbo.T  
    ```  
  
     Si la mémoire disponible est suffisante, `T_copy` peut être une table mémoire optimisée, ce qui accélère la copie des données. <sup>2</sup>  
  
5.  Supprimez les objets liés au schéma référençant la table d'origine.  
  
6.  Supprimez la table d'origine.  
  
7.  Créez la nouvelle table (`T`) avec le script qui contient le nouvel index.  
  
8.  Copiez les données de `T_copy` dans `T`.  
  
9. Recréez les objets de référencement liés au schéma et appliquez les autorisations.  
  
10. Démarrez la charge de travail sur `T`.  
  
 <sup>1</sup> notez que `T_copy` est conservé sur le disque dans cet exemple. Si une sauvegarde de `T` est disponible, `T_copy` peut être une table temporaire ou non durable.  
  
 <sup>2</sup> il doit y avoir suffisamment de mémoire pour `T_copy`. La mémoire n'est pas libérée immédiatement lors de l'exécution de `DROP TABLE`. Si la table `T_copy` est mémoire optimisée, la mémoire disponible doit être suffisante pour deux copies supplémentaires de la table `T`. Si la table `T_copy` est sur disque, la mémoire disponible doit être suffisante pour une copie supplémentaire de la table `T`, car le garbage collector doit rattraper son retard après suppression de l'ancienne version de `T`.  
  
## <a name="changing-schema-powershell"></a>Modification du schéma (PowerShell)  
 Les scripts PowerShell suivants préparent et génèrent les modifications de schéma en créant un script des autorisations de table et associées.  
  
```powershell
prepare_schema_change.ps1 <serverName> <databaseName> <schemaName> <tableName>
```
  
 Ce script accepte comme argument une table et génère le script de l'objet et de ses autorisations et des objets de référencement liés au schéma et leurs autorisations dans le dossier actif. Au total, sept scripts sont générés pour la mise à jour du schéma de la table d'entrée.  
  
-   Copiez les données dans une table temporaire (un segment mémoire).  
  
-   Supprimez les objets liés au schéma référençant la table.  
  
-   Supprimez la table.  
  
-   Recréez la table avec le nouveau schéma et réappliquez les autorisations.  
  
-   Copiez les données de la table temporaire dans la table recréée.  
  
-   Recréez les objets liés au schéma référençant la table et leurs autorisations.  
  
-   Supprimez la table temporaire.  
  
 Le script de l'étape 4 doit être mis à jour afin de refléter les modifications de schéma souhaitées. Si des modifications sont apportées aux colonnes de la table, les scripts pour les étapes 5 (copier les données de la table temporaire) et 6 (recréer des procédures stockées) doivent être mis à jour si nécessaire.  
  
```powershell
# Prepare for schema changes by scripting out the table, as well as associated permissions
# Usage: prepare_schema_change.ps1 server_name db_name schema_name table_name  
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage prepare_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
$object_heap = "$object$(Get-Random)"  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$scripter = New-Object ("Microsoft.SqlServer.Management.SMO.Scripter") ($server)  
  
## initialize table variable  
$tableUrn = $server.Databases[$database].Tables[$object, $schema]  
if($tableUrn.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
## initialize scripting object  
$scriptingOptions = New-Object ("Microsoft.SqlServer.Management.SMO.ScriptingOptions")
$scriptingOptions.Permissions = $True  
$scriptingOptions.ScriptDrops = $True  
  
$scripter.Options = $scriptingOptions;  
  
Write-Host "(1) Scripting SELECT INTO $object_heap for table [$object] to 1_copy_to_heap_for_$schema`_$object.sql"  
Echo "SELECT * INTO $schema.$object_heap FROM $schema.$object WITH (SNAPSHOT)" | Out-File "1_copy_to_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Scripting DROP for procs schema-bound to [$object] 2_drop_procs_$schema`_$object.sql"  
## query referencing schema-bound objects  
$dt = $server.Databases[$database].ExecuteWithResults("select r.referencing_schema_name, r.referencing_entity_name  
from sys.dm_sql_referencing_entities ('$schema.$object', 'OBJECT') as r join sys.sql_modules m on r.referencing_id=m.object_id  
where r.is_caller_dependent = 0 and m.is_schema_bound=1;")  
  
## initialize out file  
Echo "" | Out-File "2_drop_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script object   
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      $scripter.Script($so) | Out-File -Append "2_drop_procs_$schema`_$object.sql"  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
Write-Host "(3) Scripting DROP table for [$object] to 3_drop_table_$schema`_$object.sql"
$scripter.Script($tableUrn) | Out-File "3_drop_table_$schema`_$object.sql";
Write-Host "--done--"  
Write-Host ""  
  
## now script creates  
$scriptingOptions.ScriptDrops = $False  
  
Write-Host "(4) Scripting CREATE table and permissions for [$object] to !please_edit_4_create_table_$schema`_$object.sql"  
Write-Host "***** rename this script to 4_create_table.sql after completing the updates to the schema"
$scripter.Script($tableUrn) | Out-File "!please_edit_4_create_table_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Scripting INSERT INTO table from heap and UPDATE STATISTICS for [$object] to 5_copy_from_heap_$schema`_$object.sql"  
Write-Host "[update this script if columns are added to or removed from the table]"  
Echo "INSERT INTO [$schema].[$object] SELECT * FROM [$schema].[$object_heap]; UPDATE STATISTICS [$schema].[$object] WITH FULLSCAN, NORECOMPUTE" | Out-File "5_copy_from_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Scripting CREATE PROC and permissions for procedures schema-bound to [$object] to 6_create_procs_$schema`_$object.sql"  
Write-Host "[update the procedure definitions if columns are renamed or removed]"  
## initialize out file  
Echo "" | Out-File "6_create_procs_$schema`_$object.sql"  
## loop through schema-bound objects  
ForEach ($t In $dt.Tables)  
{    
   ForEach ($r In $t.Rows)  
   {    
      ## script the schema-bound object  
      $so =  $server.Databases[$database].StoredProcedures[$r[1], $r[0]]  
      ForEach($s In $scripter.Script($so))  
        {  
            Echo $s | Out-File -Append "6_create_procs_$schema`_$object.sql"  
            Echo "GO" | Out-File -Append "6_create_procs_$schema`_$object.sql"  
        }  
   }  
}  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Scripting DROP $object_heap to 7_drop_heap_$schema`_$object.sql"  
Echo "DROP TABLE $schema.$object_heap" | Out-File "7_drop_heap_$schema`_$object.sql";  
Write-Host "--done--"  
Write-Host ""  
```  
  
 Le script PowerShell suivant exécute les modifications de schéma qui ont fait l'objet d'un script dans l'exemple précédent. Ce script accepte comme argument une table et exécute les scripts de modification de schéma qui ont été générés pour cette table et les procédures stockées associées.  
  
 Utilisation : execute_schema_change. ps1 *nom_serveur * * db_name `schema_name`table_name*  
  
```powershell
# stop execution once an error occurs  
$ErrorActionPreference="Stop"  
  
if($args.Count -le 3)  
{  
   throw "Usage execute_schema_change.ps1 server_name db_name schema_name table_name"  
}  
  
$servername = $args[0]  
$database = $args[1]  
$schema = $args[2]  
$object = $args[3]  
  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.SMO") | Out-Null  
  
$server =  New-Object ("Microsoft.SqlServer.Management.SMO.Server") ($servername)  
$database = $server.Databases[$database]  
$table = $database.Tables[$object, $schema]  
if($table.Count -eq 0)  
{  
   throw "Table or database not found"  
}  
  
$1 = Get-Item "1_copy_to_heap_$schema`_$object.sql"  
$2 = Get-Item "2_drop_procs_$schema`_$object.sql"  
$3 = Get-Item "3_drop_table_$schema`_$object.sql"  
$4 = Get-Item "4_create_table_$schema`_$object.sql"  
$5 = Get-Item "5_copy_from_heap_$schema`_$object.sql"  
$6 = Get-Item "6_create_procs_$schema`_$object.sql"  
$7 = Get-Item "7_drop_heap_$schema`_$object.sql"  
  
Write-Host "(1) Running SELECT INTO heap for table [$object] from 1_copy_to_heap_for_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $1.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(2) Running DROP for procs schema-bound from [$object] 2_drop_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $2.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(3) Running DROP table for [$object] to 4_drop_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $3.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(4) Running CREATE table and permissions for [$object] from 4_create_table_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $4.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(5) Running INSERT INTO table from heap for [$object] and UPDATE STATISTICS from 5_copy_from_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $5.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(6) Running CREATE PROC and permissions for procedures schema-bound to [$object] from 6_create_procs_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $6.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
  
Write-Host "(7) Running DROP heap from 7_drop_heap_$schema`_$object.sql"  
$database.ExecuteNonQuery("$(Echo $7.OpenText().ReadToEnd())")  
Write-Host "--done--"  
Write-Host ""  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tables optimisées en mémoire](memory-optimized-tables.md)  
