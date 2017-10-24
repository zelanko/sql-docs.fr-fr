---
title: '@@VERSION (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 09/18/2017
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
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: c9fc3634abc5ca23c96f46adf2a52881ee15c40c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40version---transact-sql-configuration-functions"></a>& #x 40 ; & #x 40 ; Version - Transact SQL les fonctions de Configuration
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne des informations système et de build pour l'installation actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
  


