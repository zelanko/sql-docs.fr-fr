---
title: sp_db_selective_xml_index (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_db_selective_xml_index_TSQL
- sp_db_selective_xml_index
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_selective_xml_index procedure
ms.assetid: 017301a2-4a23-4e68-82af-134f3d4892b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e9b1752b5e567c2a26080422874e5bf6e31bc568
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528601"
---
# <a name="spdbselectivexmlindex-transact-sql"></a>sp_db_selective_xml_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Active ou désactive la fonctionnalité d'index XML sélectif sur une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Appelée sans paramètres, la procédure stockée retourne 1 si l'index XML sélectif est activé sur une base de données particulière.  
  
> [!NOTE]  
>  Afin de désactiver l’Index XML sélectif à l’aide de cette procédure stockée, la base de données doit être placée en mode de récupération simple à l’aide de la [Options ALTER DATABASE SET &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) commande.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
  
      sys.sp_db_selective_xml_index[[ @db_name = ] 'db_name'],   
[[ @action = ] 'action']  
```  
  
## <a name="arguments"></a>Arguments  
`[ @ db_name = ] 'db_name'` Le nom de la base de données pour activer ou désactiver des Index XML sélectif sur. Si *db_name* est NULL, la base de données en cours est supposé.  
  
`[ @action = ] 'action'` Détermine s’il faut activer ou désactiver l’index. Si une valeur autre que 'on', 'true', 'off' ou 'false' est passée, une erreur sera déclenchée.  
  
```  
  
Allowed values: 'on', 'off', 'true', 'false'  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **1** si l’Index XML sélectif est activé sur une base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-enable-selective-xml-index-functionality"></a>A. Activer la fonctionnalité d'index XML sélectif  
 L'exemple suivant active l'index XML sélectif sur la base de données active.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'on';  
GO  
```  
  
 L'exemple suivant active l'index XML sélectif sur la base de données AdventureWorks2012.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'true';  
GO  
```  
  
### <a name="b-disable-selective-xml-index-functionality"></a>B. Désactiver la fonctionnalité d'index XML sélectif  
 L'exemple suivant désactive l'index XML sélectif sur la base de données active.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'off';  
GO  
```  
  
 L'exemple suivant désactive l'index XML sélectif sur la base de données AdventureWorks2012.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'false';  
GO  
```  
  
### <a name="c-detect-if-selective-xml-index-is-enabled"></a>C. Détecter si l'index XML sélectif est activé  
 L'exemple suivant détecte si l'index XML sélectif est activé. Retourne 1 si l'index XML sélectif est activé.  
  
```  
EXECUTE sys.sp_db_selective_xml_index;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Index XML sélectifs &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  
