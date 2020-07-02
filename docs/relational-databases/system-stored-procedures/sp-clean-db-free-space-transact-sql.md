---
title: sp_clean_db_free_space (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_clean_db_free_space_TSQL
- sp_clean_db_free_space
dev_langs:
- TSQL
helpviewer_keywords:
- sp_clean_db_free_space
- ghost records
ms.assetid: faa96f7e-be92-47b1-8bc5-4dbba5331655
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1622f7cd1d14e83d76ef9cebc716b2743e288395
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771298"
---
# <a name="sp_clean_db_free_space-transact-sql"></a>sp_clean_db_free_space (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Supprime des informations qui sont restées sur les pages de la base de données en raison des routines de modification de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. sp_clean_db_free_space nettoie toutes les pages de tous les fichiers de la base de données.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_clean_db_free_space   
[ @dbname ] = 'database_name'   
[ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @dbname =] '*database_name*'  
 Nom de la base de données à nettoyer. *dbname* est de **type sysname** et ne peut pas avoir la valeur null.  
  
 [ @cleaning_delay =] '*delay_in_seconds*'  
 Spécifie un intervalle entre le nettoyage des pages. Cela réduit l'effet sur le système d'E/S. *delay_in_seconds* est de **type int** avec 0 comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Les opérations de suppression d’une table ou de mise à jour qui entraînent le déplacement d’une ligne peuvent libérer immédiatement de l’espace sur une page en supprimant les références à la ligne. Cependant, dans certains cas, la ligne peut physiquement être conservée sur la page de données sous la forme d'un enregistrement fantôme. Les enregistrements fantômes sont supprimés régulièrement par un processus en arrière-plan. Ces données résiduelles ne sont pas retournées par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] en réponse aux requêtes. Cependant, dans des environnements dans lesquels la sécurité physique des données ou des fichiers de sauvegarde est menacée, vous pouvez utiliser sp_clean_db_free_space pour nettoyer ces enregistrements fantômes.  
  
 La durée d'exécution de sp_clean_db_free_space dépend de la taille du fichier, de l'espace disponible et de la capacité du disque. Dans la mesure où l'exécution de sp_clean_db_free_space peut affecter de manière significative l'activité d'E/S, il est recommandé d'exécuter cette procédure en dehors des heures d'activité.  
  
 Avant d'exécuter sp_clean_db_free_space, il est recommandé de créer une sauvegarde de base de données complète.  
  
 La procédure stockée [sp_clean_db_file_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md) associée peut nettoyer un fichier unique.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle de base de données db_owner.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant nettoie toutes les informations résiduelles de la base de données `AdventureWorks2012`.  
  
```  
USE master;  
GO  
EXEC sp_clean_db_free_space   
@dbname = N'AdventureWorks2012' ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de base de données des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)
 <br>[Guide de processus de nettoyage fantôme](../ghost-record-cleanup-process-guide.md) 
  
  
