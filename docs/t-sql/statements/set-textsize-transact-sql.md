---
title: SET TEXTSIZE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTSIZE_TSQL
- TEXTSIZE
- SET_TEXTSIZE_TSQL
- SET TEXTSIZE
dev_langs:
- TSQL
helpviewer_keywords:
- SET TEXTSIZE statement
- SELECT statement [SQL Server], text size returned
- size [SQL Server], text and image data
- TEXTSIZE option
- text size returned [SQL Server]
ms.assetid: 787154a6-39a6-4dd6-a6d0-67b4364f95d5
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d9925b382a7d09722846ca7da583fb92fe4609c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-textsize-transact-sql"></a>SET TEXTSIZE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Spécifie la taille de **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **texte**, **ntext**, et **image** les données retournées par une instruction SELECT.  
  
> [!IMPORTANT]  
>  **ntext**, **texte**, et **image** des types de données seront supprimées dans une future version de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser ces types de données dans un nouveau développement. Prévoyez de modifier les applications qui les utilisent actuellement. Utilisez plutôt les types de données **nvarchar(max)**, **varchar(max)**et **varbinary(max)** .  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SET TEXTSIZE { number }   
```  
  
## <a name="arguments"></a>Arguments  
 *nombre*  
 Est la longueur de **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **texte**, **ntext**, ou **image** données, en octets. *nombre* est un entier dont la valeur maximale est 2147483647 (2 Go).  La valeur -1 indique une taille illimitée. La valeur 0 rétablit la taille de la valeur par défaut de 4 Ko.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (10.0 et versions ultérieures) et le pilote ODBC pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifier automatiquement `-1` (illimité) quand la connexion.  
  
 **Pilotes antérieurs à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 :** le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB (version 9) pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatiquement 2147483647 à set TEXTSIZE lors de la connexion.  
  
## <a name="remarks"></a>Notes  
 La définition de SET TEXTSIZE affecte le @@TEXTSIZE (fonction).  
  
 L'option SET TEXTSIZE est définie lors de l'exécution, et non pas durant l'analyse.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

