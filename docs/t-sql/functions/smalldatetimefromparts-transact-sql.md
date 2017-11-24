---
title: SMALLDATETIMEFROMPARTS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SMALLDATETIMEFROMPARTS
- SMALLDATETIMEFROMPARTS_TSQL
dev_langs: TSQL
helpviewer_keywords: SMALLDATETIMEFROMPARTS function
ms.assetid: 7467fdab-e588-419c-9e29-42caec34a9ea
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 07eaaf385e0227f3e5ddf7d0c1ee506aecca211a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="smalldatetimefromparts-transact-sql"></a>SMALLDATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Retourne un **smalldatetime** valeur pour la date et heure spécifiées.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SMALLDATETIMEFROMPARTS ( year, month, day, hour, minute )  
```  
  
## <a name="arguments"></a>Arguments  
 *année*  
 Expression entière spécifiant une année.  
  
 *mois*  
 Expression entière spécifiant un mois.  
  
 *jour*  
 Expression entière spécifiant un jour.  
  
 *heure*  
 Expression entière spécifiant des heures.  
  
 *minute*  
 Expression entière spécifiant des minutes.  
  
## <a name="return-types"></a>Types de retour  
 **smalldatetime**  
  
## <a name="remarks"></a>Notes  
 Cette fonction agit comme un constructeur pour complètement initialisée **smalldatetime** valeur. Si les arguments ne sont pas valides, une erreur est générée. Si les arguments obligatoires sont NULL, la valeur NULL est retournée.  
  
 Cette fonction peut être exécutée à distance sur des serveurs [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et versions ultérieures. Il n’est pas exécutée à distance sur les serveurs disposant d’une version antérieure [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="examples"></a>Exemples  
  
```  
SELECT SMALLDATETIMEFROMPARTS ( 2010, 12, 31, 23, 59 ) AS Result  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------------------  
2011-01-01 00:00:00  
  
(1 row(s) affected)  
```  
  

