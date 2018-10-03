---
title: sp_help_fulltext_catalogs_cursor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_catalogs_cursor
- sp_help_fulltext_catalogs_cursor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_catalogs_cursor
ms.assetid: d44478d1-0cc4-415e-9d1a-6dccb64674fa
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 53c4b27fe3907b4098f5b4ef1bcce83eec416ddd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702247"
---
# <a name="sphelpfulltextcatalogscursor-transact-sql"></a>sp_help_fulltext_catalogs_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Utilise un curseur pour retourner l'ID, le nom, le répertoire racine, l'état et le nombre de tables indexées en texte intégral du catalogue de texte intégral spécifié.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez le [sys.fulltext_catalogs](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md) vue de catalogue à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_fulltext_catalogs_cursor [ @cursor_return= ] @cursor_variable OUTPUT ,   
     [ @fulltext_catalog_name = ] 'fulltext_catalog_name'   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@cursor_return=**] *@cursor_variable* **SORTIE**  
 Variable de sortie de type **curseur**. Le curseur est en lecture seule, dynamique et permet les défilements.  
  
 [  **@fulltext_catalog_name=**] **'***fulltext_catalog_name***'**  
 Nom du catalogue de texte intégral. *fulltext_catalog_name* est **sysname**. Si ce paramètre est omis ou s'il a la valeur NULL, des informations sur tous les catalogues de texte intégral associés à la base de données en cours sont retournées.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**fulltext_catalog_id**|**smallint**|Identificateur du catalogue de texte intégral.|  
|**NOM**|**sysname**|Nom du catalogue de texte intégral.|  
|**PATH**|**nvarchar(260)**|À partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], cette clause n'a aucun effet.|  
|**ÉTAT**|**Int**|État du remplissage de l'index de recherche en texte intégral du catalogue :<br /><br /> 0 = Inactif <br /><br /> 1 = Remplissage complet en cours<br /><br /> 2 = En pause <br /><br /> 3 = Accéléré<br /><br /> 4 = Récupération<br /><br /> 5 = Arrêt<br /><br /> 6 = Remplissage incrémentiel en cours<br /><br /> 7 = Indexation en cours<br /><br /> 8 = Disque plein Suspendu<br /><br /> 9 = Suivi des modifications|  
|**NUMBER_FULLTEXT_TABLES**|**Int**|Nombre de tables indexées en texte intégral associées au catalogue.|  
  
## <a name="permissions"></a>Permissions  
 Les autorisations d'exécution reviennent par défaut au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 Cet exemple retourne des informations sur le catalogue de texte intégral `Cat_Desc`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_catalogs_cursor @mycursor OUTPUT, 'Cat_Desc';  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>Voir aussi  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_catalog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql.md)   
 [sp_help_fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
