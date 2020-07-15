---
title: Charger des fichiers dans FileTables | Microsoft Docs
description: Découvrez comment charger et migrer des fichiers dans FileTables sous SQL Server lorsque les fichiers sont stockés de différentes façons. En savoir plus sur les opérations de chargement en masse.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], migrating files
- FileTables [SQL Server], bulk loading
- FileTables [SQL Server], loading files
ms.assetid: dc842a10-0586-4b0f-9775-5ca0ecc761d9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8be4fbed43f4d54fb199b687a3409337ded3ff3b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767965"
---
# <a name="load-files-into-filetables"></a>Charger des fichiers dans FileTables
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Explique comment charger ou migrer des fichiers dans FileTables.  
  
##  <a name="loading-or-migrating-files-into-a-filetable"></a><a name="BasicsLoadNew"></a> Chargement ou migration de fichiers dans un FileTable  
 La méthode que vous choisissez pour le chargement ou la migration de fichiers dans un FileTable dépend de l'emplacement de stockage actuel des fichiers.  
  
|Emplacement actuel des fichiers|Options de migration|  
|-------------------------------|---------------------------|  
|Les fichiers sont actuellement stockés dans le système de fichiers.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a aucune connaissance des fichiers.|Étant donné qu'un FileTable s'affiche en tant que dossier dans le système de fichiers Windows, vous pouvez charger facilement des fichiers dans un nouveau FileTable en faisant appel à l'une des méthodes disponibles pour le déplacement ou la copie de fichiers. Ces méthodes incluent l’Explorateur Windows, les options de ligne de commande, notamment xcopy et robocopy, ainsi que les applications ou les scripts personnalisés.<br /><br /> Il est impossible de convertir un dossier existant en FileTable.|  
|Les fichiers sont actuellement stockés dans le système de fichiers.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient une table de métadonnées qui contient des pointeurs sur les fichiers.|La première étape consiste à déplacer ou à copier les fichiers à l’aide de l’une des méthodes indiquées plus haut.<br /><br /> La deuxième étape consiste à mettre à jour la table de métadonnées existante de sorte qu'elle pointe sur le nouvel emplacement des fichiers.<br /><br /> Pour plus d’informations, consultez [Exemple : migration de fichiers à partir du système de fichiers dans un FileTable](#HowToMigrateFiles) dans cet article.|  
  
###  <a name="how-to-load-files-into-a-filetable"></a><a name="HowToLoadNew"></a> Procédure : charger des fichiers dans un FileTable  
Vous pouvez appliquer les méthodes suivantes pour charger des fichiers dans un FileTable :  
  
-   Faites glisser et déplacez des fichiers depuis les dossiers source vers le nouveau dossier FileTable dans l'Explorateur Windows.  
  
-   Utilisez les options de ligne de commande telles que MOVE, COPY, XCOPY ou ROBOCOPY de l’invite de commandes ou dans un fichier de commandes ou un script.  
  
-   Écrivez une application personnalisée pour déplacer ou copier les fichiers en C# ou Visual Basic.NET. Appelez des méthodes à partir de l’espace de noms **System.IO**.  
  
###  <a name="example-migrating-files-from-the-file-system-into-a-filetable"></a><a name="HowToMigrateFiles"></a> Exemple : migration de fichiers à partir du système de fichiers dans un FileTable  
 Dans ce scénario, vos fichiers sont stockés dans le système de fichiers et vous disposez d'une table de métadonnées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contient des pointeurs sur les fichiers. Vous souhaitez déplacer les fichiers dans un FileTable, puis remplacer le chemin UNC d'origine pour chaque fichier dans les métadonnées par le chemin UNC de FileTable. La fonction [GetPathLocator &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getpathlocator-transact-sql.md) vous aide à accomplir cet objectif.  
  
 Pour cet exemple, supposez qu'il existe une table de base de données nommée **PhotoMetadata**qui contient des données relatives à des photographies. Cette table comprend une colonne **UNCPath** du type **varchar**(512) qui contient le chemin UNC réel à un fichier .jpg.  
  
 Pour migrer les fichiers image du système de fichiers vers un FileTable, vous devez effectuer les opérations suivantes :  
  
1.  Créez un nouveau FileTable pour contenir les fichiers. Cet exemple utilise le nom de la table, **dbo.PhotoTable**, mais ne fournit pas le code permettant de créer la table.  
  
2.  Utilisez xcopy ou un outil similaire pour copier les fichiers .jpg, avec leur structure de répertoire, dans le répertoire racine du FileTable.  
  
3.  Corrigez les métadonnées dans la table **PhotoMetadata**, en utilisant du code semblable à l’exemple suivant :  

```sql  
--  Add a path locator column to the PhotoMetadata table.  
ALTER TABLE PhotoMetadata ADD pathlocator hierarchyid;  
  
-- Get the root path of the Photo directory on the File Server.  
DECLARE @UNCPathRoot varchar(100) = '\\RemoteShare\Photographs';  
  
-- Get the root path of the FileTable.  
DECLARE @FileTableRoot varchar(1000);  
SELECT @FileTableRoot = FileTableRootPath('dbo.PhotoTable');  
  
-- Update the PhotoMetadata table.  
  
-- Replace the File Server UNC path with the FileTable path.  
UPDATE PhotoMetadata  
    SET UNCPath = REPLACE(UNCPath, @UNCPathRoot, @FileTableRoot);  
  
-- Update the pathlocator column to contain the pathlocator IDs from the FileTable.  
UPDATE PhotoMetadata  
    SET pathlocator = GetPathLocator(UNCPath);  
```  
  
##  <a name="bulk-loading-files-into-a-filetable"></a><a name="BasicsBulkLoad"></a> Chargement en masse de fichiers dans un FileTable  
 Un FileTable se comporte comme une table normale pour les opérations en bloc, avec les caractéristiques suivantes :  
  
 Un FileTable a des contraintes définies par le système qui garantissent le maintien de l’intégrité de l’espace de noms de fichier/répertoire. Ces contraintes doivent être vérifiées sur le volume de données chargé dans le FileTable. Puisque certaines opérations d'insertion en masse permettent d'ignorer les contraintes de table, les conditions requises suivantes sont appliquées.  
  
-   Les opérations de chargement en masse qui appliquent des contraintes peuvent être exécutées sur un FileTable comme sur toute autre table. Cette catégorie comprend les opérations suivantes :  
  
    -   bcp avec clause CHECK_CONSTRAINTS.  
  
    -   BULK INSERT avec clause CHECK_CONSTRAINTS.  
  
    -   INSERT INTO ... SELECT * FROM OPENROWSET(BULK ...) sans clause IGNORE_CONSTRAINTS.  
  
-   Les opérations de chargement en masse qui n'imposent pas de contraintes échouent à moins que les contraintes de FileTable définies par le système aient été désactivées. Cette catégorie comprend les opérations suivantes :  
  
    -   bcp sans clause CHECK_CONSTRAINTS.  
  
    -   BULK INSERT sans clause CHECK_CONSTRAINTS.  
  
    -   INSERT INTO ... SELECT * FROM OPENROWSET(BULK ...) avec clause IGNORE_CONSTRAINTS.  
  
###  <a name="how-to-bulk-load-files-into-a-filetable"></a><a name="HowToBulkLoad"></a> Procédure : charger des fichiers en masse dans un FileTable  
 Vous pouvez faire appel à différentes méthodes pour charger en masse des fichiers dans un FileTable :  
  
-   **bcp**  
  
    -   Effectuez un appel avec la clause **CHECK_CONSTRAINTS** .  
  
    -   Désactivez l’espace de noms FileTable et effectuez un appel sans la clause **CHECK_CONSTRAINTS** . Ensuite, réactivez l'espace de noms FileTable.  
  
-   **BULK INSERT**  
  
    -   Effectuez un appel avec la clause **CHECK_CONSTRAINTS** .  
  
    -   Désactivez l’espace de noms FileTable et effectuez un appel sans la clause **CHECK_CONSTRAINTS** . Ensuite, réactivez l'espace de noms FileTable.  
  
-   **INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...)**  
  
    -   Effectuez un appel avec la clause **IGNORE_CONSTRAINTS** .  
  
    -   Désactivez l’espace de noms FileTable et effectuez un appel sans la clause **IGNORE_CONSTRAINTS** . Ensuite, réactivez l'espace de noms FileTable.  
  
 Pour plus d’informations sur la désactivation des contraintes FileTable, consultez [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md).  
  
###  <a name="how-to-disable-filetable-constraints-for-bulk-loading"></a><a name="disabling"></a> Procédure : désactiver les contraintes de FileTable pour le chargement en masse  
 Pour charger en masse des fichiers dans un FileTable sans la surcharge liée à l'application des contraintes définies par le système, vous pouvez désactiver temporairement les contraintes. Pour plus d’informations, consultez [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder aux FileTables avec Transact-SQL](../../relational-databases/blob/access-filetables-with-transact-sql.md)   
 [Accéder aux FileTables avec des API d’entrée-sortie de fichier](../../relational-databases/blob/access-filetables-with-file-input-output-apis.md)  
  
  
