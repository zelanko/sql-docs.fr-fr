---
title: "Créer une table pour le stockage de données FILESTREAM | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], table storage
ms.assetid: 029c3059-5c83-43e2-a859-9027031b7de1
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7dd390bcb61a1e8f320fb6aa3a4c0209dfab3d77
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-table-for-storing-filestream-data"></a>Créer une table pour le stockage de données FILESTREAM
  Cette rubrique indique comment créer une table pour stocker des données FILESTREAM.  
  
 Lorsque la base de données comporte un groupe de fichiers FILESTREAM, vous pouvez créer ou modifier des tables pour stocker des données FILESTREAM. Pour spécifier qu’une colonne contient des données FILESTREAM, créez une colonne **varbinary(max)** et ajoutez l’attribut FILESTREAM.  
  
### <a name="to-create-a-table-to-store-filestream-data"></a>Pour créer une table pour stocker des données FILESTREAM  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez sur **Nouvelle requête** pour afficher l'Éditeur de requête.  
  
2.  Copiez le code [!INCLUDE[tsql](../../includes/tsql-md.md)] de l'exemple suivant dans l'éditeur de requête. Ce code [!INCLUDE[tsql](../../includes/tsql-md.md)] crée une table compatible FILESTREAM appelée Enregistrements.  
  
3.  Pour créer la table, cliquez sur **Exécuter**.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment créer une table nommée `Records`. La colonne `Id` est une colonne `ROWGUIDCOL` requise pour utiliser des données FILESTREAM avec les API Win32. La colonne `SerialNumber` est une colonne `UNIQUE INTEGER`. La colonne `Chart` est une colonne `FILESTREAM` qui sert à stocker `Chart` dans le système de fichiers.  
  
> [!NOTE]  
>  Cette rubrique fait référence à la base de données Archive créée dans [Créer une base de données compatible FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md).  
  
 [!code-sql[FILESTREAM#FS_CreateTable](../../relational-databases/blob/codesnippet/tsql/create-a-table-for-stori_1.sql)]  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
