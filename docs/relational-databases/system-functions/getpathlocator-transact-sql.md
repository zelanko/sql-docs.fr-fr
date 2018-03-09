---
title: GetPathLocator (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetPathLocator
- GetPathLocator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetPathLocator function
ms.assetid: 78b7e220-445b-4fdf-811b-7253f4f2b058
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a94f9be78e3acf4d5ea91ec3f538a021890aff16
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="getpathlocator-transact-sql"></a>GetPathLocator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne la valeur d'ID de localisateur de chemin d'accès pour le fichier ou le répertoire spécifié d'un FileTable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GetPathLocator(filenamespace_path)  
```  
  
## <a name="arguments"></a>Arguments  
 *filenamespace_path*  
 Chemin d'accès à l'espace de noms dans le FileTable. Le chemin d’accès de l’espace de noms est de type **nvarchar (max)**.  
  
 Lorsque la base de données appartient à un groupe de disponibilité Always On, le **GetPathLocator** fonction accepte le nom de réseau virtuel (VNN) ou le nom de l’ordinateur.  
  
## <a name="return-type"></a>Type de retour  
 **hierarchyid**  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Pour plus d'informations, consultez [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
## <a name="examples"></a>Exemples  
 Vous pouvez utiliser la **GetPathLocator** fonction lorsque vous avez des fichiers de migration à partir d’un serveur de fichiers à un FileTable. Dans ce cas, vous souhaitez déplacer les fichiers dans le FileTable, puis remplacer le chemin d'accès UNC d'origine de chaque fichier par le chemin d'accès UNC de FileTable. Pour obtenir un exemple complet, consultez [charger des fichiers dans FileTables](../../relational-databases/blob/load-files-into-filetables.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Travailler avec des répertoires et des chemins d'accès dans FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
