---
title: sp_addmergealternatepublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergealternatepublisher_TSQL
- sp_addmergealternatepublisher
helpviewer_keywords:
- sp_addmergealternatepublisher
ms.assetid: de46e0b1-d946-4021-bff6-2d8e3187656d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 21d0ea34f3521333976ce00a3f5b823c3fcb816a
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54129299"
---
# <a name="spaddmergealternatepublisher-transact-sql"></a>sp_addmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute la possibilité pour un Abonné d'utiliser un partenaire de synchronisation alternatif. Les propriétés de publication doivent spécifier que les Abonnés peuvent opérer des synchronisations avec d'autres serveurs de publication. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addmergealternatepublisher [ @publisher= ] 'publisher'  
          , [ @publisher_db= ] 'publisher_db'  
          , [ @publication= ] 'publication'  
          , [ @alternate_publisher= ] 'alternate_synchronization_partner'  
          , [ @alternate_publisher_db= ] 'alternate_publisher_db'  
          , [ @alternate_publication= ] 'alternate_synchronization_partner'  
     , [ @alternate_distributor= ] 'alternate_distributor'   
    [ , [ @friendly_name= ] 'friendly_name' ]   
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publisher=**] **'**_publisher_**'**  
 Nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
 [  **@publisher_db=**] **'**_publisher_db_**'**  
 Nom de la base de données de publication. *publisher_db* est **sysname**, sans valeur par défaut.  
  
 [  **@publication=**] **'**_publication_**'**  
 Nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@alternate_publisher=**] **'**_alternate_synchronization_partner_**'**  
 Est le nom de l’autre serveur de publication. *alternate_synchronization_partner* est **sysname**, sans valeur par défaut.  
  
 [  **@alternate_publisher_db=**] **'**_alternate_publisher_db_**'**  
 Nom de la base de données de publication sur le serveur de publication de remplacement. *alternate_publisher_db* est **sysname**, sans valeur par défaut.  
  
 [  **@alternate_publication=**] **'**_alternate_synchronization_partner_**'**  
 Nom de la publication sur le partenaire de synchronisation de remplacement. *alternate_synchronization_partner* est **sysname**, sans valeur par défaut.  
  
 [  **@alternate_distributor=**] **'**_alternate_distributor_**'**  
 Nom du serveur de distribution pour le partenaire de synchronisation de remplacement. *alternate_distributor* est **sysname**, sans valeur par défaut.  
  
 [  **@friendly_name=**] **'**_friendly_name_**'**  
 Nom d'affichage permettant d'identifier l'association du serveur de publication, de la publication et du serveur de distribution constituant un partenaire de synchronisation secondaire. *nom_convivial* est **nvarchar (255)**, avec NULL comme valeur par défaut.  
  
 [  **@reserved=**] **'**_réservé_**'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addmergealternatepublisher** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addmergealternatepublisher**.  
  
## <a name="see-also"></a>Voir aussi  
 [la procédure sp_dropmergealternatepublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergealternatepublisher-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
