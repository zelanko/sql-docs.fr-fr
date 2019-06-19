---
title: Créer une base de données compatible FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FILESTREAM-enabled databases
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 810b1d36eefb99d6e1bcf855dc7710495429751a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66010317"
---
# <a name="create-a-filestream-enabled-database"></a>Créer une base de données compatible FILESTREAM
  Cette rubrique montre comment créer une base de données qui prend en charge FILESTREAM. Étant donné que FILESTREAM utilise un type de groupe de fichiers spécial, lors de la création de la base de données vous devez spécifier la clause CONTAINS FILESTREAM pour au moins un groupe de fichiers.  
  
 Un groupe de fichiers FILESTREAM peut contenir plusieurs fichiers. Pour obtenir un exemple de code qui illustre la création d’un groupe de fichiers FILESTREAM contenant plusieurs fichiers, consultez [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
### <a name="to-create-a-filestream-enabled-database"></a>Pour créer une base de données compatible FILESTREAM  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez sur **Nouvelle requête** pour afficher l'Éditeur de requête.  
  
2.  Copie le [!INCLUDE[tsql](../../includes/tsql-md.md)] code crée une base de données compatible FILESTREAM appelée Archive.  
  
    > [!NOTE]  
    >  Pour ce script, le répertoire C:\Data doit exister.  
  
3.  Pour générer la base de données, cliquez sur **Exécuter**.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant crée une base de données nommée `Archive`. La base de données contient trois groupes de fichiers : `PRIMARY`, `Arch1`et `FileStreamGroup1`. `PRIMARY` et `Arch1` sont des groupes de fichiers ordinaires qui ne peuvent pas contenir de données FILESTREAM. `FileStreamGroup1` est le groupe de fichiers `FILESTREAM` .  
  
```sql  
CREATE DATABASE Archive   
ON  
PRIMARY ( NAME = Arch1,  
    FILENAME = 'c:\data\archdat1.mdf'),  
FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
    FILENAME = 'c:\data\filestream1')  
LOG ON  ( NAME = Archlog1,  
    FILENAME = 'c:\data\archlog1.ldf')  
GO  
```  
  
 Pour un groupe de fichiers `FILESTREAM` , `FILENAME` fait référence à un chemin d'accès. Le chemin d'accès jusqu'au dernier dossier doit exister, et le dernier dossier ne doit pas exister. Dans cet exemple, `c:\data` doit exister. Toutefois, le sous-dossier `filestream1` ne peut pas exister lorsque vous exécutez l'instruction `CREATE DATABASE` . Pour plus d’informations sur la syntaxe, consultez [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
 Après l'exécution de l'exemple précédent, un fichier filestream.hdr et un dossier $FSLOG apparaissent dans le dossier c:\Data\filestream1. Le fichier filestream.hdr est un fichier d'en-tête pour le conteneur FILESTREAM.  
  
> [!IMPORTANT]  
>  Le fichier filestream.hdr est un fichier système important. Il contient des informations d'en-tête FILESTREAM. Vous ne devez ni le supprimer, ni le modifier.  
  
 Pour les bases de données existantes, vous pouvez utiliser l'instruction [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) pour ajouter un groupe de fichiers FILESTREAM.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
