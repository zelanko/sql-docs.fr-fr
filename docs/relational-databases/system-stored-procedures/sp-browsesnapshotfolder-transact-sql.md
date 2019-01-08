---
title: sp_browsesnapshotfolder (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsesnapshotfolder
- sp_browsesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsesnapshotfolder
ms.assetid: 0872edf2-4038-4bc1-a68d-05ebfad434d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1bd85e4d3e76df8cf5fe0b30350fb1a02959516f
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591153"
---
# <a name="spbrowsesnapshotfolder-transact-sql"></a>sp_browsesnapshotfolder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le chemin d'accès complet du dernier instantané généré pour une publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_browsesnapshotfolder [@publication= ] 'publication'  
    { [ , [ @subscriber = ] 'subscriber' ]  
 [ , [ @subscriber_db = ] 'subscriber_db' ] }  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'**_publication_**'**  
 Nom de la publication contenant l'article. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@subscriber=**] **'**_abonné_**'**  
 Nom de l'Abonné. *abonné* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@subscriber_db=**] **'**_bd_abonné_**'**  
 Est le nom de la base de données d’abonnement. *bd_abonné* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar(512)**|Chemin d'accès complet du répertoire de l'instantané.|  
  
## <a name="remarks"></a>Notes  
 **sp_browsesnapshotfolder** est utilisé dans la réplication d’instantané ou transactionnelle.  
  
 Si le *abonné* et *bd_abonné* champs conservent la valeur NULL, la procédure stockée retourne le dossier d’instantanés de l’instantané le plus récent disponible pour la publication. Si le *abonné* et *bd_abonné* les champs sont spécifiés, la procédure stockée retourne le dossier d’instantanés pour l’abonnement spécifié. Si aucun instantané n'a été généré pour la publication, un jeu de résultats vide est retourné.  
  
 Si la publication est configurée de sorte à générer les fichiers d'instantané dans le répertoire de travail du serveur de publication et dans son dossier d'instantané, le jeu de résultats comporte deux lignes. La première ligne contient le dossier d'instantané de la publication, la seconde le répertoire de travail du serveur de publication. **sp_browsesnapshotfolder** est utile pour déterminer le répertoire où les fichiers d’instantanés sont générés.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_browsesnapshotfolder**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
