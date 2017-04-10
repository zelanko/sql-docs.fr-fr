---
title: "D&#233;placer une base de donn&#233;es compatible FILESTREAM | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FILESTREAM [SQL Server], déplacement d’une base de données compatible FILESTREAM"
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# D&#233;placer une base de donn&#233;es compatible FILESTREAM
  Cette rubrique montre comment déplacer une base de données compatible FILESTREAM.  
  
> [!NOTE]  
>  Les exemples de cette rubrique exigent la base de données Archive créée dans [Créer une base de données compatible FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md).  
  
### Pour déplacer une base de données compatible FILESTREAM  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez sur **Nouvelle requête** pour ouvrir l’Éditeur de requête.  
  
2.  Copiez le script [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant dans l’Éditeur de requête, puis cliquez sur **Exécuter**. Ce script affiche l'emplacement des fichiers de base de données physiques utilisés par la base de données FILESTREAM.  
  
    ```tsql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  Copiez le script [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant dans l’Éditeur de requête, puis cliquez sur **Exécuter**. Ce code met la base de données `Archive` hors connexion.  
  
    ```tsql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  Créez le dossier `C:\moved_location` dans lequel vous allez placer les fichiers et les dossiers listés à l'étape 2.  
  
5.  Copiez le script [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant dans l’Éditeur de requête, puis cliquez sur **Exécuter**. Ce script met la base de données `Archive` en ligne.  
  
    ```tsql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## Voir aussi  
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  