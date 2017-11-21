---
title: NEWSEQUENTIALID (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/08/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEWSEQUENTIALID
- NEWSEQUENTIALID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEWSEQUENTIALID function
- GUIDs [SQL Server]
ms.assetid: e06d2cab-f1ff-42f1-8550-6aaec57be36f
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 39bd8a393a9cc3e19e457cda98c0521492e07911
ms.contentlocale: fr-fr
ms.lasthandoff: 10/24/2017

---
# <a name="newsequentialid-transact-sql"></a>NEWSEQUENTIALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crée une valeur GUID supérieure à celle d'un GUID précédemment généré par cette fonction sur un ordinateur donné depuis le démarrage de Windows. Après le redémarrage de Windows, le GUID peut redémarrer à partir d'une plage inférieure, mais est toujours globalement unique. Lorsqu'une colonne GUID est utilisée comme identificateur de ligne, l'utilisation de NEWSEQUENTIALID peut être plus rapide que celle de la fonction NEWID. Cela est dû au fait que la fonction NEWID génère une activité aléatoire et utilise moins de pages de données mises en cache. L'utilisation de NEWSEQUENTIALID vous aide également à remplir complètement les pages de données et d'index.  
  
> [!IMPORTANT]  
>  Si la confidentialité des données pose un problème, n'utilisez pas cette fonction. Il est possible de deviner la valeur du GUID généré suivant, et donc d'accéder aux données qui lui sont associées.  
  
 NEWSEQUENTIALID est un wrapper sur les fenêtres [UuidCreateSequential](http://go.microsoft.com/fwlink/?LinkId=164027) fonction, avec certaines [octets mélange appliqué](https://blogs.msdn.microsoft.com/dbrowne/2012/07/03/how-to-generate-sequential-guids-for-sql-server-in-net/).
  
> [!WARNING]  
>  La fonction UuidCreateSequential possède des dépendances de matériel. Sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], peuvent développer des clusters de valeurs séquentielles lorsque les bases de données (par exemple, des bases de données) sont déplacés vers d’autres ordinateurs. Lorsque vous utilisez Always On et sur [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)], les clusters de valeurs séquentielles peuvent développer si la base de données bascule vers un autre ordinateur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NEWSEQUENTIALID ( )  
```  
  
## <a name="return-type"></a>Type de retour  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Notes  
 NEWSEQUENTIALID() peut uniquement être utilisé avec les contraintes par défaut sur les colonnes de table de type **uniqueidentifier**. Exemple :  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT NEWSEQUENTIALID());   
```  
  
 Lorsque vous utilisez la fonction NEWSEQUENTIALID() dans des expressions DEFAULT, vous ne pouvez pas la combiner avec d'autres opérateurs scalaires. Par exemple, vous ne pouvez pas exécuter ce qui suit :  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT dbo.myfunction(NEWSEQUENTIALID()));  
```  
  
 Dans l'exemple précédent, `myfunction()` est une fonction scalaire définie par l'utilisateur qui accepte et renvoie une valeur de type `uniqueidentifier`.  
  
 La fonction NEWSEQUENTIALID ne peut pas être référencée dans les requêtes.  
  
 Vous pouvez utiliser NEWSEQUENTIALID pour générer des GUID afin de réduire les fractionnements de pages et l'E/S aléatoire au niveau feuille des index.  
  
 Chaque GUID généré à l'aide de NEWSEQUENTIALID est unique sur cet ordinateur. Les GUID générés à l'aide de la fonction NEWSEQUENTIALID sont uniques sur plusieurs ordinateurs seulement si l'ordinateur source possède une carte réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [NEWID &#40; Transact-SQL &#41;](../../t-sql/functions/newid-transact-sql.md)   
 [Opérateurs de comparaison &#40; Transact-SQL &#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md)  
  
  

