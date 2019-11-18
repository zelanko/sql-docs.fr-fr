---
title: CREATE WORKLOAD CLASSIFIER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD CLASSIFIER
- WORKLOAD_CLASSIFIER_TSQL
- CREATE WORKLOAD CLASSIFIER
- CREATE_WORKLOAD_CLASSIFIER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: adf8b1e04e7dcd75bcad0c4b184ae60f2b59d248
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056491"
---
# <a name="create-workload-classifier-transact-sql"></a>CREATE WORKLOAD CLASSIFIER (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Crée un objet classifieur à utiliser dans la gestion des charges de travail.  Le classifieur affecte les requêtes entrantes à un groupe de charge de travail en fonction des paramètres spécifiés dans la définition d’instruction du classifieur.  Les classifieurs sont évalués avec chaque requête envoyée.  Si une requête ne correspond pas à un classifieur, elle est affectée au groupe de charge de travail par défaut.  Le groupe de charge de travail par défaut est la classe de ressources smallrc.

> [!NOTE]
> Le classifieur de charge de travail prend la place de l’affectation de la classe de ressources sp_addrolemember.  Une fois que vous avez créé les classifieurs de charge de travail, exécutez sp_droprolemember pour supprimer tous les mappages de classes de ressources redondants.

 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe

```
CREATE WORKLOAD CLASSIFIER classifier_name  
WITH  
    (   WORKLOAD_GROUP = ‘name’  
    ,   MEMBERNAME = ‘security_account’ 
[ [ , ] WLM_LABEL = ‘label’ ]  
[ [ , ] WLM_CONTEXT = ‘context’ ]  
[ [ , ] START_TIME = ‘HH:MM’ ]  
[ [ , ] END_TIME = ‘HH:MM’ ]  
  
[ [ , ] IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH }]) 
[;]
```

## <a name="arguments"></a>Arguments

 *classifier_name*  
 Spécifie le nom qui identifie le classifieur de charge de travail.  classifier_name est de type sysname.  Il peut comporter jusqu’à 128 caractères et doit être unique dans l’instance.

 *WORKLOAD_GROUP* =  *'name'*    
 Quand les conditions sont remplies par les règles du classifieur, le paramètre 'name' mappe la requête à un groupe de charge de travail.  name est de type sysname.  Il peut comporter jusqu’à 128 caractères et doit être un nom de groupe de charge de travail valide au moment de la création du classifieur.

 Les groupes de charge de travail disponibles se trouvent dans la vue de catalogue [sys.workload_management_workload_groups](../../relational-databases/system-catalog-views/sys-workload-management-workload-groups-transact-sql.md).

 *MEMBERNAME* ='security_account'*    
 Il s’agit du compte de sécurité ajouté au rôle.  security_account est de type sysname, sans valeur par défaut. security_account peut être un utilisateur de base de données, un rôle de base de données, une connexion Azure Active Directory ou un groupe Azure Active Directory.
 
 *WLM_LABEL*   
 Spécifie la valeur de l’étiquette utilisée pour classifier une requête.  L’étiquette est un paramètre facultatif de type nvarchar(255).  Ajoutez [OPTION (LABEL)](/azure/sql-data-warehouse/sql-data-warehouse-develop-label) dans la requête pour qu’elle corresponde à la configuration du classifieur.

Exemple :

```sql
CREATE WORKLOAD CLASSIFIER wcELTLoads WITH  
( WORKLOAD_GROUP = 'wgDataLoad'
 ,MEMBERNAME     = 'ELTRole'  
 ,WLM_LABEL      = 'dimension_loads' )

SELECT COUNT(*) 
  FROM DimCustomer
  OPTION (LABEL = 'dimension_loads')
```

*WLM_CONTEXT*  
Spécifie la valeur du contexte de session utilisée pour classifier une requête.  Le contexte est un paramètre facultatif de type nvarchar(255).  Utilisez [sys.sp_set_session_context](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md?view=azure-sqldw-latest) avec le nom de variable `wlm_context` avant d’envoyer une requête pour définir le contexte de session.

Exemple :

```sql
CREATE WORKLOAD CLASSIFIER wcDataLoad WITH  
( WORKLOAD_GROUP = 'wgDataLoad'
 ,MEMBERNAME     = 'ELTRole'
 ,WLM_CONTEXT    = 'dim_load' )
 
--set session context
EXEC sys.sp_set_session_context @key = 'wlm_context', @value = 'dim_load'

--run multiple statements using the wlm_context setting
SELECT COUNT(*) FROM stg.daily_customer_load
SELECT COUNT(*) FROM stg.daily_sales_load

--turn off the wlm_context session setting
EXEC sys.sp_set_session_context @key = 'wlm_context', @value = null
```

*START_TIME* et *END_TIME*  
Spécifie les valeurs start_time et end_time utilisées pour classifier une requête.  Les deux valeurs start_time et end_time sont au format HH:MM dans le fuseau horaire UTC.  Elles doivent être spécifiées ensemble.

Exemple :

```sql
CREATE WORKLOAD CLASSIFIER wcELTLoads WITH  
( WORKLOAD_GROUP = 'wgDataLoads'
 ,MEMBERNAME     = 'ELTRole'  
 ,START_TIME     = '22:00'
 ,END_TIME       = '02:00' )
```

*IMPORTANCE* = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH }  
Spécifie l’importance relative d’une requête.  Elle prend l'une des valeurs suivantes :

- LOW
- BELOW_NORMAL
- NORMAL (valeur par défaut)
- ABOVE_NORMAL
- HIGH  

Si l’importance n’est pas spécifiée, le paramètre d’importance défini pour le groupe de charge de travail est appliqué.  L’importance par défaut du groupe de charge de travail est définie sur Normal.  L’importance impacte l’ordre dans lequel les requêtes sont planifiées, avec un accès prioritaire aux ressources et aux verrous.

## <a name="classification-parameter-precedence"></a>Précédence des paramètres de classification

Une requête peut être mise en correspondance avec plusieurs classifieurs.  Les paramètres de classifieur sont définis avec une précédence.  Le classifieur correspondant à la précédence la plus élevée est utilisé en premier pour affecter un groupe de charge de travail et une importance.  La précédence s’établit comme suit :
1. Utilisateur
2. ROLE
3. WLM_LABEL
4. WLM_SESSION
5. START_TIME/END_TIME

Examinez les configurations de classifieurs suivantes.

```sql
CREATE WORKLOAD CLASSIFIER classiferA WITH  
( WORKLOAD_GROUP = 'wgDashboards'  
 ,MEMBERNAME     = 'userloginA'
 ,IMPORTANCE     = HIGH
 ,WLM_LABEL      = 'salereport' )

CREATE WORKLOAD CLASSIFIER classiferB WITH  
( WORKLOAD_GROUP = 'wgUserQueries'  
 ,MEMBERNAME     = 'userloginA'
 ,IMPORTANCE     = LOW
 ,START_TIME     = '18:00')
 ,END_TIME       = '07:00' )
```

L’utilisateur `userloginA` est configuré pour les deux classifieurs.  Si userloginA exécute une requête ayant l’étiquette `salesreport` entre 18 h 00 et 7 h, la requête sera classifiée dans le groupe de charge de travail wgDashboards avec une importance élevée (HIGH).  Vous voudrez peut-être classifier cette requête dans le groupe wgUserQueries avec une faible importance (LOW) pour la création de rapports durant les heures creuses, mais la précédence de WLM_LABEL est supérieure à START_TIME/END_TIME.  Dans ce cas, vous pouvez ajouter START_TIME/END_TIME à classiferA.

 Pour plus d’informations, consultez la [classification de la charge de travail](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification#classification-precedence).

## <a name="permissions"></a>Autorisations

 Exige l’autorisation CONTROL DATABASE.  
  
## <a name="examples"></a>Exemples

 L'exemple suivant montre comment créer un classifieur de charge de travail appelé `wgcELTRole`. Il utilise le groupe de charge de travail staticrc20 et l’utilisateur `ELTRole`, et définit l’importance sur `above_normal`.

```sql
CREATE WORKLOAD CLASSIFIER wgcELTRole
  WITH (WORKLOAD_GROUP = 'staticrc20'
       ,MEMBERNAME = 'ELTRole'
      ,IMPORTANCE = above_normal);
```

## <a name="see-also"></a>Voir aussi

[Classification de SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)</br>
[DROP WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-classifier-transact-sql.md)</br>
[sys.workload_management_workload_classifiers](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifiers-transact-sql.md)</br>
[sys.workload_management_workload_classifier_details](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifier-details-transact-sql.md)

