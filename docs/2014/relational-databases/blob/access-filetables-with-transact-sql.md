---
title: Accéder aux FileTables avec Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FileTables [SQL Server], accessing files with T-SQL
ms.assetid: 3c4a5ffb-c521-4696-99cb-2b03cffc9c02
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 4e99d1aa8564c5a69c19c4b8275e0397595d69ea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044244"
---
# <a name="access-filetables-with-transact-sql"></a>Accéder aux FileTables avec Transact-SQL
  Décrit le fonctionnement des commandes de langage de manipulation de données (DML) [!INCLUDE[tsql](../../includes/tsql-md.md)] avec des FileTables.  
  
##  <a name="BasicsInsert"></a> Opérations INSERT sur les FileTables  
 Les points suivants s'appliquent aux opérations **INSERT** sur les FileTables :  
  
-   Toutes les colonnes d'attribut de fichier ont des contraintes NOT NULL. Si les valeurs ne sont pas définies explicitement, les valeurs par défaut appropriées sont fournies.  
  
-   Les contraintes définies par le système sont appliquées si l’instruction INSERT définit les valeurs **name**, **path_locator**, **parent_path_locator**, ou les attributs de fichier.  
  
-   L’application peut obtenir la valeur **path_locator** pour un fichier ou un répertoire en fournissant le chemin d’accès au système de fichiers à la fonction [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql).  
  
##  <a name="BasicsUpdate"></a> Opérations UPDATE sur les FileTables  
 Les points suivants s'appliquent aux opérations **UPDATE** sur les FileTables :  
  
-   Les mises à jour apportées aux données définies par l'utilisateur sont autorisées.  
  
-   Les contraintes définies par le système sont appliquées si l’instruction INSERT définit les valeurs **name**, **path_locator**, **parent_path_locator**, ou les attributs de fichier.  
  
-   Les mises à jour peuvent être apportées aux données FILESTREAM dans la colonne **file_stream** sans affecter aucune des autres colonnes, dont les horodateurs.  
  
##  <a name="BasicsDelete"></a> Opérations DELETE sur les FileTables  
 Les points suivants s'appliquent aux opérations **DELETE** sur les FileTables :  
  
-   La suppression d'une ligne supprime également le fichier ou répertoire correspondant du système de fichiers.  
  
-   La suppression d'une ligne échoue si la ligne correspond à un répertoire qui contient d'autres fichiers ou répertoires.  
  
##  <a name="BasicsConstraints"></a> Contraintes appliquées pour les opérations DML sur les FileTables  
 Les contraintes définies par le système garantissent que les actions DML ne compromettent pas l'intégrité de la hiérarchie de l'espace de noms de fichier. Les contraintes appliquées sont les suivantes :  
  
-   Lorsque vous définissez ou modifiez le **nom** du fichier ou du répertoire :  
  
    -   Les conventions d'affectation des noms de fichiers Windows et de répertoires sont appliquées.  
  
    -   Le système impose l'unicité du nom dans le répertoire parent.  
  
-   Quand vous définissez ou modifiez l’emplacement d’un fichier ou d’un répertoire en définissant ou en modifiant la valeur **path_locator** ou **parent_path_locator**:  
  
    -   L'unicité est appliquée.  
  
    -   La cohérence de l’arborescence hiérarchique des répertoires et des fichiers est appliquée, notamment la cohérence des valeurs **path_locator** et **parent_path_locator** .  
  
-   **is_directory** ne peut pas prendre la valeur True quand la colonne **file_stream** n’est pas Null. Les données de la colonne **file_stream** indiquent que la ligne représente un fichier et pas un répertoire.  
  
-   Les colonnes d'attributs de fichier ne peuvent pas être Null. Les contraintes NOT NULL sont appliquées avec des valeurs par défaut.  
  
-   La valeur de **last_access_time** ne peut pas être antérieure à **last_write_time** et **creation_time**.  
  
## <a name="see-also"></a>Voir aussi  
 [Charger des fichiers dans FileTables](load-files-into-filetables.md)   
 [Travailler avec des répertoires et des chemins d'accès dans FileTables](work-with-directories-and-paths-in-filetables.md)   
 [Accéder aux FileTables avec des API d’entrée-sortie de fichier](access-filetables-with-file-input-output-apis.md)   
 [DDL, fonctions, procédures stockées et vues FileTable](../views/views.md)  
  
  
