---
title: SET FIPS_FLAGGER (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FIPS_FLAGGER
- SET_FIPS_FLAGGER_TSQL
- FIPS_FLAGGER_TSQL
- SET FIPS_FLAGGER
dev_langs:
- TSQL
helpviewer_keywords:
- SET FIPS_FLAGGER statement
- FIPS 127-2 standard
- FIPS_FLAGGER option
ms.assetid: e82f6bee-6cf6-4061-be22-9ad2e8e9d3d6
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4c28fd5419aec8bf15745150288b6878fd65ac1f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-fipsflagger-transact-sql"></a>SET FIPS_FLAGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Spécifie la vérification de conformité à la norme FIPS 127-2. Ce contrôle est basé sur la norme ISO. Pour plus d’informations sur la conformité aux normes FIPS SQL Server, consultez [l’utilisation de SQL Server 2016 dans le mode FIPS 140-2-conformes](https://support.microsoft.com/help/4014354/how-to-use-sql-server-2016-in-fips-140-2-compliant-mode). 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SET FIPS_FLAGGER ( 'level' |  OFF )  
```  
  
## <a name="arguments"></a>Arguments  
 **'** *niveau* **'**  
 Niveau de conformité à la norme FIPS 127-2, vérifié dans toutes les opérations effectuées dans les bases de données. Si une opération de base de données est en conflit avec le niveau des normes ISO choisi, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un avertissement.  
  
 *niveau* doit être une des valeurs suivantes.  
  
|Valeur| Description|  
|-----------|-----------------|  
|ENTRY|Vérification des normes pour la conformité ISO de base.|  
|FULL|Vérification des normes pour la conformité ISO complète.|  
|INTERMEDIATE|Vérification des normes pour la conformité ISO de niveau intermédiaire.|  
|OFF|Pas de vérification des normes.|  
  
## <a name="remarks"></a>Notes  
 Le paramètre de `SET FIPS_FLAGGER` est définie au moment de l’analyse et pas lors de l’exécution ou d’exécution. Paramètre au moment de l’analyse signifie que si l’instruction SET est présente dans le lot ou une procédure stockée, elle devient effective, indépendamment de si l’exécution du code ait réellement atteint ce point ; et la `SET` instruction devient effective avant toutes les instructions sont exécutées. Par exemple, même si le `SET` instruction se trouve dans un `IF...ELSE` bloc d’instructions qui n’est jamais atteint pendant l’exécution, le `SET` prend quand même effet parce que le `IF...ELSE` bloc d’instructions est analysé.  
  
 Si `SET FIPS_FLAGGER` est définie dans une procédure stockée, la valeur de `SET FIPS_FLAGGER` est rétablie une fois le contrôle est retourné à partir de la procédure stockée. Par conséquent, un `SET FIPS_FLAGGER` instruction spécifiée en SQL dynamique n’a pas d’effet sur les instructions qui suivent l’instruction SQL dynamique.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

