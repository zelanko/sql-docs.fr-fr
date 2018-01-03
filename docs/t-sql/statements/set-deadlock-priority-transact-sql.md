---
title: SET DEADLOCK_PRIORITY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET DEADLOCK_PRIORITY
- DEADLOCK_PRIORITY_TSQL
- SET_DEADLOCK_PRIORITY_TSQL
- DEADLOCK_PRIORITY
dev_langs: TSQL
helpviewer_keywords:
- deadlocks [SQL Server], priority settings
- DEADLOCK_PRIORITY option
- locking [SQL Server], deadlocks
- priority deadlock settings [SQL Server]
- SET DEADLOCK_PRIORITY statement
ms.assetid: 810a3a8e-3da3-4bf9-bb15-7b069685a1b6
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b80f18cb5440560b34924cad619af1f195f49a47
ms.sourcegitcommit: ed9335fe62c0c8d94ee87006c6957925d09ee301
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="set-deadlockpriority-transact-sql"></a>SET DEADLOCK_PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Indique l'importance relative liée à la poursuite du traitement par la session active si cette dernière est bloquée avec une autre session.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET DEADLOCK_PRIORITY { LOW | NORMAL | HIGH | <numeric-priority> | @deadlock_var | @deadlock_intvar }  
  
<numeric-priority> ::= { -10 | -9 | -8 | … | 0 | … | 8 | 9 | 10 }  
```  
  
## <a name="arguments"></a>Arguments  
 LOW  
 Indique que la session active sera la victime de l'interblocage si elle est impliquée dans un interblocage et si la valeur de la priorité des autres sessions impliquées dans la chaîne d'interblocage est définie sur NORMAL ou HIGH ou sur une valeur entière supérieure à 5. La session active ne sera pas la victime du blocage si les priorités des autres sessions sont définies sur une valeur entière inférieure à 5. Indique également que la session active est éligible pour être la victime du blocage si la priorité d'une autre session est définie sur LOW ou sur une valeur entière égale à -5.  
  
 NORMAL  
 Indique que la session active sera la victime de l'interblocage si la valeur de la priorité des autres sessions impliquées dans la chaîne d'interblocage est définie sur HIGH ou sur une valeur entière supérieure à 0, mais elle ne sera pas une victime de l'interblocage si la valeur de priorité d'une autre session est définie sur LOW ou sur une valeur entière inférieure à 0. Indique également que la session active est éligible pour être la victime du blocage si la priorité d'une autre session est définie sur NORMAL ou sur une valeur entière égale à 0. La valeur de la priorité par défaut est NORMAL.  
  
 HIGH  
 Indique que la session active sera la victime du blocage si la valeur de la priorité des autres sessions impliquées dans la chaîne de blocage est un entier supérieur à 5, ou qu'elle est éligible pour être la victime du stockage si la priorité d'une autre session est également définie sur HIGH ou sur une valeur entière égale à 5.  
  
 \<priorité numérique >  
 Plage de valeurs entières (-10 à 10) pour fournir 21 niveaux de priorité de blocage. Indique que la session active sera la victime du blocage si la valeur de la priorité de blocage des autres sessions de la chaîne de blocage est supérieure et qu'elle ne sera pas la victime du blocage si la valeur de la priorité de blocage des autres sessions est inférieure. Indique également que la session active est éligible pour être la victime du blocage si la valeur de la priorité d'une autre session est identique. LOW correspond à -5, NORMAL à 0 et HIGH à 5.  
  
 **@***deadlock_var*  
 Variable de type chaîne de caractères spécifiant la priorité du blocage. La valeur de la variable doit être définie sur « LOW' », « NORMAL » ou « HIGH ». Elle doit être suffisamment importante pour contenir toute la chaîne.  
  
 **@***deadlock_intvar*  
 Variable de type entier spécifiant la priorité du blocage. Elle doit être définie sur une valeur entière comprise dans la plage (-10 - 10)  
  
## <a name="remarks"></a>Notes   
 Un blocage se produit lorsque deux sessions sont en attente d'un accès aux ressources verrouillées par l'autre session. Si une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] détecte le blocage de deux sessions, l'une des sessions est choisie comme victime du blocage afin de résoudre ce problème. La transaction active de la victime est annulée et le message d'erreur 1205 est retourné au client. Tous les verrous détenus par cette session sont libérés et le traitement des autres sessions peut se poursuivre.  
  
 La session choisie comme victime du blocage varie en fonction de la priorité de blocage des deux sessions :  
  
-   Si la valeur de la priorité de blocage des deux sessions est identique, l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] choisit la session pour laquelle l'annulation est la moins onéreuse comme victime du blocage. Par exemple, si la priorité des deux sessions est définie sur HIGH, l'instance choisit comme victime la session pour laquelle l'annulation est la moins coûteuse (estimation). Le coût est déterminé en comparant le nombre d’octets du journal écrit à ce stade dans chaque transaction. (Vous pouvez voir cette valeur comme « Utilisé du journal » dans un graphique de blocage).
  
-   Si les priorités de blocage des sessions sont différentes, la session dont la priorité de blocage est inférieure est choisie comme victime du blocage.  
  
 L'option SET DEADLOCK_PRIORITY est définie lors de l'exécution, et non pas durant l'analyse.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise une variable pour définir la priorité de blocage sur `LOW`.  
  
```  
DECLARE @deadlock_var NCHAR(3);  
SET @deadlock_var = N'LOW';  
  
SET DEADLOCK_PRIORITY @deadlock_var;  
GO  
```  
  
 L'exemple suivant définit la priorité de blocage sur `NORMAL`.  
  
```  
SET DEADLOCK_PRIORITY NORMAL;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [@@LOCK_TIMEOUT &#40;Transact-SQL&#41;](../../t-sql/functions/lock-timeout-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET LOCK_TIMEOUT &#40; Transact-SQL &#41;](../../t-sql/statements/set-lock-timeout-transact-sql.md)  
  
  
