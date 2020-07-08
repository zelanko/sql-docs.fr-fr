---
title: Importer en bloc des données LOB au moyen du fournisseur d’ensembles de lignes en bloc OPENROWSET
description: Le fournisseur d’ensembles de lignes SQL Server OPENROWSET permet d’importer en bloc des données LOB. Les types pris en charge sont varbinary(max), varchar(max) et nvarchar(max).
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- SINGLE_NCLOB option
- bulk rowset providers [SQL Server]
- bulk importing [SQL Server], data formats
- OPENROWSET function, bulk importing large data
- SINGLE_CLOB option
- data formats [SQL Server], large-object data
- large data, bulk imports
- SINGLE_BLOB option
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 3c998b1efeb6fff7726161ffb02e240e8a8847f1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85640708"
---
# <a name="bulk-import-large-object-data-with-openrowset-bulk-rowset-provider-sql-server"></a>Importer en bloc des données LOB au moyen du fournisseur d’ensembles de lignes en bloc OPENROWSET (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Le fournisseur d'ensembles de lignes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET vous permet d'importer en bloc un fichier de données en données LOB.  
  
 Les types de données LOB pris en charge par le fournisseur d’ensembles de lignes OPENROWSET sont **varbinary**(max) ou **image**, **varchar**(max) ou **text**et **nvarchar**(max) ou **ntext**.  
  
> [!NOTE]  
>  Les types de données **image**, **text** et **ntext** sont déconseillés.  
  
 La clause OPENROWSET BULK prend en charge trois options pour importer le contenu d'un fichier de données sous forme d'un ensemble d'une seule ligne et d'une seule colonne. Vous pouvez spécifier une de ces options au lieu d'utiliser un fichier de format. Ces options sont les suivantes :  
  
 SINGLE_BLOB  
 Lit le contenu de *data_file* comme une seule ligne, retourne le contenu comme un ensemble de lignes à une seule colonne de type **varbinary(max)** .  
  
 SINGLE_CLOB  
 Lit le contenu du fichier de données spécifié comme des caractères, retourne le contenu sous la forme d’un ensemble de lignes à une seule ligne et une seule colonne de type **varchar(max)** en utilisant le classement de la base de données actuelle (texte ou document [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word).  
  
 SINGLE_NCLOB  
 Lit le contenu du fichier de données spécifié comme de l’unicode, retourne le contenu sous la forme d’un ensemble de lignes à une seule ligne et une seule colonne de type **nvarchar(max)** en utilisant le classement de la base de données active.  
  
## <a name="see-also"></a>Voir aussi  
 [Importer des données en bloc à l’aide de BULK INSERT ou OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)   
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)  
  
  
