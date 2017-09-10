---
title: '@@VERSION (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@VERSION'
- '@@VERSION_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@VERSION function'
- current SQL Server installation information
- versions [SQL Server], @@VERSION
- processors [SQL Server], types
ms.assetid: 385ba80e-7c28-41a5-9cdb-5648f3785983
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b8367bb24a37996b2956e3107113812a32086fed
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="version---transact-sql-configuration-functions"></a>Version - Transact SQL les fonctions de Configuration
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne des informations système et de build pour l'installation actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
@@VERSION  
```  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar**  
  
## <a name="remarks"></a>Notes  
 Le @@VERSION résultats sont présentés comme une seule chaîne nvarchar. Vous pouvez utiliser la [SERVERPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/serverproperty-transact-sql.md) fonction pour récupérer les valeurs de propriété.  
  
 Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les informations suivantes sont retournées.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Version  
  
-   Architecture du processeur  
  
-   Date de build de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Déclaration de copyright  
  
-   Édition de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
-   Version du système d'exploitation  
  
 Pour [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], les informations suivantes sont retournées.  
  
-   Édition- « Microsoft Azure SQL Database »  
  
-   Niveau du produit- « (CTP) » ou « (RTM) »  
  
-   Version du produit  
  
-   Date de génération  
  
-   Déclaration de copyright  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-return-the-current-version-of-includessnoversionincludesssnoversion-mdmd"></a>R : retourner la version actuelle de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 L'exemple suivant retourne les informations de version de l'installation actuelle.  
  
```  
SELECT @@VERSION AS 'SQL Server Version';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-return-the-current-version-of-includessdwincludesssdw-mdmd"></a>B. Retourner la version actuelle de[!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
  
```  
SELECT @@VERSION AS 'SQL Server PDW Version';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  


