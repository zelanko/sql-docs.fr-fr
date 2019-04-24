---
title: CREATE WORKLOAD CLASSIFIER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2019
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
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: dd10a628e5a60487ceaf11a6dd39f781fbc41596
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2019
ms.locfileid: "59581213"
---
# <a name="create-workload-classifier-transact-sql-preview"></a>CREATE WORKLOAD CLASSIFIER (Transact-SQL) (Préversion)

> [!Note]
> La classification de la charge de travail est disponible en préversion sur SQL Data Warehouse Gen2. La préversion Classification et importance de la gestion de la charge de travail s’adresse aux builds avec une date de publication du 9 avril 2019 ou une version ultérieure.  Les utilisateurs doivent éviter d’utiliser des builds antérieures à cette date pour le test de la gestion de la charge de travail.  Pour déterminer si votre build est compatible avec la gestion de la charge de travail, exécutez select @@version lorsque vous êtes connecté à votre instance SQL Data Warehouse.

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Crée un classifieur de gestion des charges de travail.  Le classifieur affecte les requêtes entrantes à un groupe de charge de travail et affecte l’importance en fonction des paramètres spécifiés dans la définition d’instruction du classifieur.  Les classifieurs sont évalués avec chaque requête envoyée.  Si une requête ne correspond pas à un classifieur, elle est affectée au groupe de charge de travail par défaut.  Le groupe de charge de travail par défaut est la classe de ressources smallrc.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône de lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe

```
CREATE WORKLOAD CLASSIFIER classifier_name  
WITH  
    ( WORKLOAD_GROUP = 'name'  
     ,MEMBERNAME = 'security_account'
 [ [ , ] IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL (default) | ABOVE_NORMAL | HIGH }])
[;]
```

## <a name="arguments"></a>Arguments

 *classifier_name*  
 Spécifie le nom qui identifie le classifieur de charge de travail.  classifier_name est de type sysname.  Il peut comporter jusqu’à 128 caractères et doit être unique dans l’instance.

WORKLOAD_GROUP = *'name'* Quand les conditions sont remplies par les règles du classifieur, le paramètre 'name' mappe la requête à un groupe de charge de travail.  name est de type sysname.  Il peut comporter jusqu’à 128 caractères et doit être un nom de groupe de charge de travail valide au moment de la création du classifieur.

WORKLOAD_GROUP doit correspondre à une classe de ressources existante :

|Classes de ressources statiques|Classes de ressources dynamiques|
|------------------------|-----------------------|
|staticrc10|smallrc|
|staticrc20|mediumrc|
|staticrc30|largerc|
|staticrc40|xlargerc|
|staticrc50||
|staticrc60||
|staticrc70||
|staticrc80||

MEMBERNAME = *'security_account'* Il s’agit du compte de sécurité ajouté au rôle.  security_account est de type sysname, sans valeur par défaut. security_account peut être un utilisateur de base de données, un rôle de base de données, une connexion Azure Active Directory ou un groupe Azure Active Directory.

IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH } Spécifie l’importance relative d’une requête.  Elle prend l'une des valeurs suivantes :

- LOW
- BELOW_NORMAL
- NORMAL (valeur par défaut)
- ABOVE_NORMAL
- HIGH  

L’importance détermine l’ordre dans lequel les requêtes sont planifiées, ce qui offre un premier accès aux ressources et aux verrous.

Si un utilisateur est membre de plusieurs rôles avec des classes de ressources différentes affectées ou mises en correspondance dans plusieurs classifieurs, l’utilisateur reçoit l’affectation de classe de ressources la plus élevée. Pour plus d’informations, consultez la [classification de la charge de travail](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification#classification-precedence)

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

## <a name="see-also"></a> Voir aussi

[DROP WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-classifier-transact-sql.md)</br>
Vue de catalogue [sys.workload_management_workload_classifier_details](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifier-details-transact-sql.md)</br>
Vue de catalogue [sys.workload_management_workload_classifiers](../../relational-databases/system-catalog-views/sys-workload-management-workload-classifiers-transact-sql.md)
[Classification de SQL Data Warehouse](/azure/sql-data-warehouse/classification)
