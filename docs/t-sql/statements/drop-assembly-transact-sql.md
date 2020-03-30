---
title: DROP ASSEMBLY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP ASSEMBLY
- DROP_ASSEMBLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- deleting assemblies
- assemblies [CLR integration], removing
- dropping assemblies
- WITH NO DEPENDENTS option
ms.assetid: 452d181a-a8e6-44a3-975d-29966d01b18d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6b5b788ef8978ce88fdb3d8aa0567724023fd5cc
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67984284"
---
# <a name="drop-assembly-transact-sql"></a>DROP ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un assembly et tous les fichiers associés dans la base de données active. Les assemblys sont créés à l’aide de [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md) et modifiés à l’aide de [ALTER ASSEMBLY](../../t-sql/statements/alter-assembly-transact-sql.md).  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DROP ASSEMBLY [ IF EXISTS ] assembly_name [ ,...n ]  
[ WITH NO DEPENDENTS ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *IF EXISTS*  
 **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] à la [version actuelle](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Supprime de manière conditionnelle l’assembly, uniquement s’il existe déjà.  
  
 *assembly_name*  
 Nom de l'assembly à supprimer.  
  
 WITH NO DEPENDENTS  
 Si cet argument est spécifié, seul *assembly_name* est supprimé, à l’exclusion des assemblys dépendants qu’il référence. Si cet argument n’est pas spécifié, DROP ASSEMBLY supprime *assembly_name* et tous les assemblys dépendants.  
  
## <a name="remarks"></a>Notes  
 La commande DROP ASSEMBLY supprime de la base de données l'assembly spécifié et tous les fichiers associés, notamment les fichiers de code source et de débogage.  
  
 Si WITH NO DEPENDENTS n’est pas spécifié, DROP ASSEMBLY supprime *assembly_name* et tous les assemblys dépendants. Si une tentative de suppression d'assemblys dépendants échoue, DROP ASSEMBLY retourne une erreur.  
  
 DROP ASSEMBLY retourne une erreur si l'assembly est référencé par un assembly existant de la base de données ou s'il est utilisé par des fonctions CLR (Common Language Runtime), des procédures, des déclencheurs, des types ou des agrégats définis par l'utilisateur dans la base de données active.  
  
 DROP ASSEMBLY ne gêne pas le code en cours d'exécution qui fait référence à l'assembly à supprimer. Toutefois, après l'exécution de DROP ASSEMBLY, les tentatives d'appel de l'assembly supprimé échouent.  
  
## <a name="permissions"></a>Autorisations  
 Vous devez être propriétaire de l'assembly ou détenir l'autorisation CONTROL sur ce dernier.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant suppose que l'assembly `HelloWorld` existe déjà dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
DROP ASSEMBLY Helloworld ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Obtention d’informations sur les assemblys](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
