---
description: SESSION_ID (Transact-SQL)
title: SESSION_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/23/2018
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
author: VanMSFT
ms.author: vanto
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 0bb9580073a6d344f5a8455ba3941c59ac94c2ef
ms.sourcegitcommit: 1126792200d3b26ad4c29be1f561cf36f2e82e13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90076624"
---
# <a name="session_id-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Retourne l’ID de la session [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] actuelle.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Azure Synapse Analytics and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur **nvarchar(32)**.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 L’ID de session est affecté à chaque connexion utilisateur lors de l’établissement de la connexion. Il persiste pendant la durée de la connexion. Lorsque la connexion se termine, l’ID de session est libéré.  
  
 L’ID de session commence par les caractères alphabétiques « SID ». Ces derniers respectent la casse et doit être mis en majuscules lorsque l’ID de session est utilisé dans des commandes [!INCLUDE[DWsql](../../includes/dwsql-md.md)].  
  
 Vous pouvez interroger la vue [sys.dm_pdw_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) pour récupérer les mêmes informations que cette fonction.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant renvoie l’ID de la session actuelle.  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [VERSION &#40;Azure Synapse Analytics&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  
