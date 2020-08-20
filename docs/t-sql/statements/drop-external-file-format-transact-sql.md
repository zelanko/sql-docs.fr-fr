---
description: DROP EXTERNAL FILE FORMAT (Transact-SQL)
title: DROP EXTERNAL FILE FORMAT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8cf9009b-59f9-4aac-bef1-dcf2cf0708b2
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2b5a652162f8dc80c7406913bb17c6c23119153b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478848"
---
# <a name="drop-external-file-format-transact-sql"></a>DROP EXTERNAL FILE FORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Supprime un format de fichier externe PolyBase.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
-- Drop an external file format  
DROP EXTERNAL FILE FORMAT external_file_format_name  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *external_file_format_name*  
 Nom du format de fichier externe à supprimer.  
  
## <a name="metadata"></a>Métadonnées  
 Pour afficher la liste des formats de fichier externes, utilisez la vue système [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md).  
  
```sql  
SELECT * FROM sys.external_file_formats;  
```  
  
## <a name="permissions"></a>Autorisations  
 Nécessite ALTER ANY EXTERNAL FILE FORMAT.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 La suppression d’un format de fichier externe ne supprime pas les données externes.  
  
## <a name="locking"></a>Verrouillage  
 Prend un verrou partagé sur l’objet EXTERNAL FILE FORMAT.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-basic-syntax"></a>R. Utilisation de la syntaxe de base  
  
```sql  
DROP EXTERNAL FILE FORMAT myfileformat;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  

