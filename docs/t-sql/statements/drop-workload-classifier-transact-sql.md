---
title: DROP WORKLOAD CLASSIFIER (Transact-SQL) | Microsoft Docs
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
- DROP_WORKLOAD_CLASSIFIER_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD CLASSIFIER statement
ms.assetid: ''
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: a9ef53323d77f1439df5daf0fedc669fe380cb3f
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2019
ms.locfileid: "59581513"
---
# <a name="drop-workload-classifier-transact-sql-preview"></a>DROP WORKLOAD CLASSIFIER (Transact-SQL) (Préversion)

> [!Note]
> La classification de la charge de travail est disponible en préversion sur SQL Data Warehouse Gen2. La préversion Classification et importance de la gestion de la charge de travail s’adresse aux builds avec une date de publication du 9 avril 2019 ou une version ultérieure.  Les utilisateurs doivent éviter d’utiliser des builds antérieures à cette date pour le test de la gestion de la charge de travail.  Pour déterminer si votre build est compatible avec la gestion de la charge de travail, exécutez select @@version lorsque vous êtes connecté à votre instance SQL Data Warehouse.

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Supprime un classifieur de gestion des charges de travail défini par l’utilisateur existant.  
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône de lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  

```
DROP WORKLOAD CLASSIFIER classifier_name;
```

## <a name="arguments"></a>Arguments

*classifier_name*  
Spécifie le nom qui identifie le classifieur de charge de travail.  classifier_name est de type sysname.  Il peut comporter jusqu’à 128 caractères et doit être unique dans l’instance.
  
## <a name="remarks"></a>Notes 

L’instruction DROP WORKLOAD CLASSIFIER n’est pas autorisée sur les classifieurs de charge de travail système.

Si des requêtes sont en cours d’exécution ou se trouvent dans la file d’attente des requêtes dans l’état suspendu, elles conserveront leur classification et le classifieur peut être supprimé immédiatement.  La suppression et la recréation du classifieur avec une importance différente n’affectent pas une requête déjà classifiée.

## <a name="permissions"></a>Autorisations

Exige l’autorisation CONTROL DATABASE.  
  
## <a name="examples"></a>Exemples

L’exemple suivant supprime le classifieur de charge de travail nommé `wgcELTROLE`.  

```sql
DROP WORKLOAD CLASSIFIER wgcELTRole;
```

> [!NOTE]
> Une requête envoyée sans classifieur correspondant est classifiée dans le groupe de charge de travail par défaut.  Le groupe de charge de travail par défaut est la classe de ressources smallrc.
  
## <a name="see-also"></a> Voir aussi

[CREATE WORKLOAD CLASSIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-classifier-transact-sql.md)</br>
[Classification de charge de travail SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
