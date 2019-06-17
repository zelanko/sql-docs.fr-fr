---
title: Abonnés de réplication sur des tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ee585f9773858848f213b3eeef6e995aedfb53f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63250883"
---
# <a name="replication-to-memory-optimized-table-subscribers"></a>Abonnés de réplication sur des tables optimisées en mémoire
  Les tables agissant comme des abonnés de réplication transactionnelle, à l'exclusion de la réplication transactionnelle d'égal à égal, peuvent être configurées en tant que tables mémoire optimisées. Les autres configurations de réplication ne sont pas compatibles avec les tables mémoire optimisées.  
  
## <a name="configuring-a-memory-optimized-table-as-a-subscriber"></a>Configuration d'une table mémoire optimisée en tant qu'abonné  
 Pour configurer une table mémoire optimisée en tant qu'abonné, effectuez les étapes suivantes.  
  
 **Créer et activer la Publication**  
  
1.  Créer une publication  
  
2.  Ajoutez des articles à la publication. Pour le paramètre `@upd_cmd`, utilisez la convention SCALL ou SQL.  
  
    ```  
    EXEC sp_addarticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @source_owner = N'dbo',  
        @source_object = N'Mem_Table',  
        @type = N'logbased',  
        @description = null,  
        @creation_script = null,  
        @pre_creation_cmd = N'none',  
        @schema_option = 0x00000000080050DF,  
        @identityrangemanagementoption = N'manual',  
        @destination_table = N'Mem_Table',  
        @destination_owner = N'dbo',  
        @vertical_partition = N'false',  
        @ins_cmd = N'CALL sp_MSins_Mem_Table',  
        @del_cmd = N'CALL sp_MSdel_Mem_Table',  
        @upd_cmd = N'SCALL sp_MSupd_Mem_Table';  
    GO  
    ```  
  
 **Générer un instantané et régler le schéma**  
  
1.  Créez un travail instantané et générez un instantané.  
  
    ```  
    EXEC sp_addpublication_snapshot @publication = N'Publication1', @frequency_type = 1;  
    EXEC sp_startpublication_snapshot @publication = N'Publication1';  
    ```  
  
2.  Naviguez jusqu'au dossier d'instantané. L’emplacement par défaut est « C:\Program Files\Microsoft SQL Server\MSSQL12. \<INSTANCE > \MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS\\».  
  
3.  Recherchez le **. SCH** pour votre table et ouvrez-le dans Management Studio. Modifiez le schéma de la table et mettez à jour la procédure stockée comme décrit ci-dessous.  
  
     Évaluez les index définis dans le fichier IDX. Modifiez `CREATE TABLE` pour spécifier les index, les contraintes, la clé primaire et la syntaxe mémoire optimisée requis. Pour les tables mémoire optimisées, les colonnes d'index doivent être NOT NULL et les colonnes d'index des types de caractères doivent être Unicode et utiliser le classement BIN2. Voir l'exemple ci-dessous :  
  
    ```  
    SET ANSI_PADDING ON;  
    GO  
  
    SET ANSI_NULLS ON;  
    GO  
  
    SET QUOTED_IDENTIFIER ON;  
    GO  
  
    CREATE TABLE [dbo].[Mem_Table]([c1] [int] NOT NULL,  
        [c2] [float] NOT NULL,  
        [c3] [decimal](10, 2) NOT NULL,  
        [c4] [nvarchar](5) COLLATE SQL_Latin1_General_CP850_BIN2 NOT NULL,  
        INDEX [hash_index_sample_memoryoptimizedtable_c2] HASH (c2) WITH (BUCKET_COUNT = 1024),  
        INDEX [index_sample_memoryoptimizedtable_c3] NONCLUSTERED ([c3]),  
        INDEX [nvarchar_index_sample_memoryoptimizedtable_c4] ([c4]),  
        CONSTRAINT [PK_sample_memoryoptimizedtable] PRIMARY KEY NONCLUSTERED ([c1])) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA);  
    GO  
    ```  
  
4.  En cas d'utilisation de la convention SCALL pour le paramètre `@upd_cmd`, accédez au fichier de schéma (.SCH) et modifiez l'instruction de mise à jour de table dans `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]` pour supprimer les colonnes de clé primaire.  
  
     Pour prendre en charge les mises à jour de clé primaire, utilisez une procédure stockée de mise à jour personnalisée pour remplacer l'instruction de mise à jour de clé primaire, comme suit :  
  
    1.  Sélectionnez les valeurs de colonne manquantes (SCALL fournit uniquement la colonne impliquée dans l'opération de mise à jour).  
  
    2.  Supprimez l'enregistrement existant.  
  
    3.  Insérez un nouvel enregistrement avec les nouvelles valeurs fournies comprenant la nouvelle clé primaire.  
  
     La procédure de mise à jour d'origine est la suivante :  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
                   [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     Si la clé primaire ne doit jamais être mise à jour sur un serveur de publication. Commenter la mise à jour de ces colonnes dans la procédure de mise à jour comme suit :  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
    --             [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     Pour permettre la prise en charge des mises à jour dans la clé primaire, modifiez la procédure de mise à jour comme suit :  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                    @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    select  
                   @c1 = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   @c2 = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   @c3 = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   @c4 = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    from [dbo].[Mem_Table] where [c1] = @pkc1  
    if @@rowcount <> 0 begin  
            delete [dbo].[Mem_Table] where [c1] = @pkc1  
            if @@rowcount <> 0  
                   insert into [dbo].[Mem_Table]([c1],  
                           [c2],  
                           [c3],  
                           [c4]) values (  
                           @c1,  
                           @c2,  
                           @c3,  
                           @c4  
                   )   
    end  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
5.  Créer la base de données d’abonné à l’aide du **élever à l’isolement d’instantané** option et définissez le classement par défaut à Latin1_General_CS_AS_KS_WS en cas d’utilisation de types de données de caractères non Unicode.  
  
    ```  
    CREATE DATABASE [Sub]   
    CONTAINMENT = NONE   
    ON PRIMARY ( NAME = [Sub], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.mdf]),   
    FILEGROUP [mem] CONTAINS MEMORY_OPTIMIZED_DATA ( NAME = [mem],   
    FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub])  
    LOG ON ( NAME = [Sub_log], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.ldf])  
    COLLATE Latin1_General_CS_AS_KS_WS;  
  
    ALTER DATABASE [Sub] SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
    GO  
    ```  
  
6.  Appliquer le schéma à la base de données d’un abonné et enregistrez le schéma pour une utilisation ultérieure.  
  
7.  Chargez les données du serveur de publication (source) sur l'abonné. Les données ne doivent pas changer sur le serveur de publication jusqu'à ce que vous ajoutiez un abonnement.  Utilisez BCP comme indiqué ci-dessous :  
  
    ```  
    bcp Pub.dbo.Mem_Table out Mem_Table.bcp -S. -T -C1252 -n  
    bcp Sub.dbo.Mem_Table in Mem_Table.bcp -S. -T -C1252 -n  
    ```  
  
8.  Reconfigurez l'article pour désactiver les modifications de schéma sur l'abonné :  
  
    ```  
    EXEC sp_changearticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @property = N'schema_option',  
        @value = 0,  
        @force_invalidate_snapshot = 1,  
        @force_reinit_subscription = 1;  
    GO  
    ```  
  
 **Ajouter l’abonnement sans synchronisation**  
  
 Ajoutez un abonnement nosync.  
  
```  
EXEC sp_addsubscription  
    @publication = N' Publication1',  
    @subscriber = @@ServerName,  
    @destination_db = N'Sub',  
    @subscription_type = N'Push',  
    @sync_type = N'replication support only',  
    @article = N'all',  
    @update_mode = N'read only',  
    @subscriber_type = 0;  
GO  
```  
  
 Les tables mémoire optimisées doivent maintenant commencer à recevoir les mises à jour du serveur de publication.  
  
## <a name="restrictions"></a>Restrictions  
 Seule la réplication transactionnelle monodirectionnelle est prise en charge. La réplication transactionnelle d'égal à égal n'est pas prise en charge.  
  
 Les tables mémoire optimisées ne peuvent pas être publiées.  
  
 Les tables de réplication sur le serveur de distribution ne peuvent pas être configurées comme des tables mémoire optimisées.  
  
 La réplication de fusion ne peut pas inclure des tables mémoire optimisées.  
  
 Sur l'abonné, les tables impliquées dans la réplication transactionnelle peuvent être configurées en tant que tables mémoire optimisées, mais les tables d'abonné doivent répondre aux exigences des tables mémoire optimisées. Cette fonction requiert les restrictions suivantes.  
  
-   Pour créer une table mémoire optimisée sur un abonné de réplication transactionnelle, les fichiers de schéma d'instantané utilisés pour créer les tables mémoire optimisées doivent être modifiés manuellement. Pour plus d’informations, consultez [modification d’un fichier de schéma](#Schema).  
  
-   Les tables répliquées en tables mémoire optimisées sur un abonné appliquent la limite de 8060 octets par ligne des tables mémoire optimisées.  
  
-   Les tables répliquées en tables mémoire optimisées sur un abonné sont limitées aux types de données autorisés dans les tables mémoire optimisées. Pour plus d’informations, consultez [pris en charge les Types de données](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md).  
  
-   Il existe des restrictions pour la mise à jour de la clé primaire des tables répliquées en une table mémoire optimisée sur un abonné. Pour plus d’informations, consultez [réplication des modifications à une clé primaire](#PrimaryKey).  
  
-   La clé étrangère, la contrainte unique, les déclencheurs, les modifications de schéma, ROWGUIDCOL, les colonnes calculées, la compression de données, les types de données d'alias, le contrôle de version et les verrous ne sont pas pris en charge dans les tables mémoire optimisées. Pour plus d’informations, consultez [Constructions Transact-SQL non prises en charge par OLTP en mémoire](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
##  <a name="Schema"></a> Modification d'un fichier de schéma  
  
-   Les index cluster ne sont pas pris en charge. Modifiez tous les index cluster en index non cluster.  
  
-   Toutes les colonnes dans la clé d'un index doivent être spécifiées comme `NOT NULL`.  
  
-   Si vous utilisez l'option de table mémoire optimisée `DURABILITY = SCHEMA_AND_DATA` , la table doit avoir un index de clé primaire non cluster.  
  
-   ANSI_PADDING doit être activé.  
  
##  <a name="PrimaryKey"></a> Réplication des modifications à une clé primaire  
 La clé primaire d'une table mémoire optimisée ne peut pas être mise à jour. Pour répliquer une mise à jour de clé primaire sur un abonné, modifiez la procédure stockée de mise à jour pour fournir la mise à jour en tant que paire d'opérations de suppression et insertion.  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication SQL Server](sql-server-replication.md)  
  
  
