---
title: SET CONCAT_NULL_YIELDS_NULL (Transact-SQL) | Documents Microsoft
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
- CONCAT_NULL_YIELDS_NULL_TSQL
- SET CONCAT_NULL_YIELDS_NULL
- CONCAT_NULL_YIELDS_NULL
- SET_CONCAT_NULL_YIELDS_NULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_NULL_YIELDS_NULL option
- null values [SQL Server], concatenation results
- concatenation [SQL Server]
- SET CONCAT_NULL_YIELDS_NULL statement
ms.assetid: 3091b71c-6518-4eb4-88ab-acae49102bc5
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 60281ff903bf7eb04165a65e8f2b75a80f589780
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-concatnullyieldsnull-transact-sql"></a>SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Détermine si les résultats de concaténation sont considérés comme des valeurs nulles ou des chaînes vides.  
  
> [!IMPORTANT]  
>  Dans une future version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CONCAT_NULL_YIELDS_NULL sera toujours ON et toute application qui définira explicitement l'option à OFF générera une erreur. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server  
    
SET CONCAT_NULL_YIELDS_NULL { ON | OFF }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET CONCAT_NULL_YIELDS_NULL ON    
```  
  
## <a name="remarks"></a>Notes  
 Si SET CONCAT_NULL_YIELDS_NULL a la valeur ON, la concaténation d'une valeur NULL avec une chaîne retourne un résultat NULL. Par exemple, `SELECT 'abc' + NULL` donne `NULL`. Si SET CONCAT_NULL_YIELDS_NULL a la valeur OFF, la concaténation d'une valeur NULL avec une chaîne renvoie la chaîne ; la valeur NULL est considérée comme une chaîne vide. Par exemple, `SELECT 'abc' + NULL` donne `abc`.  
  
 Si SET CONCAT_NULL_YIELDS_NULL n’est pas spécifié, le paramètre de la **CONCAT_NULL_YIELDS_NULL** option de base de données s’applique.  
  
> [!NOTE]  
>  SET CONCAT_NULL_YIELDS_NULL équivaut au paramètre CONCAT_NULL_YIELDS_NULL de ALTER DATABASE.  
  
 L'option SET CONCAT_NULL_YIELDS_NULL est définie lors de l'exécution, et non pas durant l'analyse.  
  
 SET CONCAT_NULL_YIELDS_NULL doit avoir la valeur ON lors de la création ou de la modification d'index dans des colonnes calculées ou des vues indexées. Si SET CONCAT_NULL_YIELDS_NULL a la valeur OFF, toute instruction CREATE, UPDATE, INSERT ou DELETE dans des tables comportant des index de colonnes calculées ou de vues indexées échoue. Pour plus d’informations sur les paramètres des options SET requises avec les vues indexées et des index sur des colonnes calculées, consultez « Considérations lorsque vous utilisez des instructions SET » dans [instructions SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 Lorsque CONCAT_NULL_YIELDS_NULL a la valeur OFF, la concaténation de chaîne est impossible au-delà des limites du serveur.  
  
 Pour afficher la valeur actuelle de ce paramètre, exécutez la requête suivante.  
  
```  
DECLARE @CONCAT_NULL_YIELDS_NULL VARCHAR(3) = 'OFF';  
IF ( (4096 & @@OPTIONS) = 4096 ) SET @CONCAT_NULL_YIELDS_NULL = 'ON';  
SELECT @CONCAT_NULL_YIELDS_NULL AS CONCAT_NULL_YIELDS_NULL;  
  
```  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre l'utilisation des deux paramètres `SET CONCAT_NULL_YIELDS_NULL`.  
  
```  
PRINT 'Setting CONCAT_NULL_YIELDS_NULL ON';  
GO  
-- SET CONCAT_NULL_YIELDS_NULL ON and testing.  
SET CONCAT_NULL_YIELDS_NULL ON;  
GO  
SELECT 'abc' + NULL ;  
GO  
  
-- SET CONCAT_NULL_YIELDS_NULL OFF and testing.  
SET CONCAT_NULL_YIELDS_NULL OFF;  
GO  
SELECT 'abc' + NULL;   
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  

