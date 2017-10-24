---
title: GO (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- GO
- GO_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- batches [SQL Server], ending
- ending batches [SQL Server]
- GO command
ms.assetid: b2ca6791-3a07-4209-ba8e-2248a92dd738
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17b78d6ca719088ade9d54db73b8ee10ef8072a5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-utilities-statements---go"></a>Instructions d’utilitaires SQL Server - GO
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Fournit des commandes qui ne sont pas [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions, mais sont reconnues par le **sqlcmd** et **osql** utilitaires et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] éditeur de Code. Ces commandes facilitent la lisibilité et l'exécution de lots et de scripts.  
  
  GO indique la fin d’un lot de [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilitaires.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GO [count]  
```  
  
## <a name="arguments"></a>Arguments  
 *nombre*  
 Entier positif. Le lot qui précède GO sera exécuté le nombre spécifié de fois.  
  
## <a name="remarks"></a>Notes  
 GO n’est pas un [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction ; il est une commande reconnue par le **sqlcmd** et **osql** utilitaires et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] éditeur de Code.  
  
 Les utilitaires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprètent GO comme le signal qu'ils doivent envoyer le lot actuel d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le traitement en cours se compose de toutes les transactions entrées depuis la dernière commande GO ou depuis le début de la session ou du script approprié s'il s'agit de la première commande GO.  
  
 Une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] ne peut pas se trouver sur la même ligne qu'une commande GO. Toutefois, la ligne peut contenir des commentaires.  
  
 Les utilisateurs doivent se conformer aux règles en vigueur concernant les traitements. Par exemple, toute exécution d'une procédure stockée faisant suite à la première instruction d'un lot doit inclure le mot clé EXECUTE. La portée des variables locales (personnalisées) se limite à un traitement et il est impossible d'y faire référence après une commande GO.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyMsg VARCHAR(50)  
SELECT @MyMsg = 'Hello, World.'  
GO -- @MyMsg is not valid after this GO ends the batch.  
  
-- Yields an error because @MyMsg not declared in this batch.  
PRINT @MyMsg  
GO  
  
SELECT @@VERSION;  
-- Yields an error: Must be EXEC sp_who if not first statement in   
-- batch.  
sp_who  
GO  
```  
  
 Les applications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent envoyer plusieurs instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en vue de leur exécution sous forme de traitement. Les instructions du traitement sont ensuite compilées dans un plan d'exécution unique. Les programmeurs qui exécutent des instructions appropriées dans les utilitaires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou élaborent des scripts d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] à exécuter par le biais des utilitaires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisent la commande GO pour signaler la fin d'un traitement.  
  
 Les applications basées sur ODBC ou sur les API OLE DB reçoivent une erreur de syntaxe s'ils tentent d'exécuter une commande GO. Les utilitaires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'envoient jamais de commande GO au serveur.  
  
 N'utilisez pas un point-virgule comme terminateur d'instruction après GO.  
  
## <a name="permissions"></a>Permissions  
 GO est une commande d'utilitaire qui ne nécessite pas d'autorisation. Elle peut être exécutée par tout utilisateur.  
  
```  
-- Yields an error because ; is not permitted after GO  
SELECT @@VERSION;  
GO;  
```  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée deux traitements. Le premier lot contient uniquement un `USE``AdventureWorks2012` instruction pour définir le contexte de base de données. Les autres instructions utilisent une variable locale. Ainsi, toutes les déclarations de variables locales doivent être groupées en un seul traitement. Pour cela, aucune commande `GO` n'est utilisée avant la dernière instruction qui fait référence à la variable.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @NmbrPeople int  
SELECT @NmbrPeople = COUNT(*)  
FROM Person.Person;  
PRINT 'The number of people as of ' +  
      CAST(GETDATE() AS char(20)) + ' is ' +  
      CAST(@NmbrPeople AS char (10));  
GO  
```  
  
 L'exemple suivant exécute les instructions dans le lot à deux reprises.  
  
```  
SELECT DB_NAME();  
SELECT USER_NAME();  
GO 2  
```  
  
  

