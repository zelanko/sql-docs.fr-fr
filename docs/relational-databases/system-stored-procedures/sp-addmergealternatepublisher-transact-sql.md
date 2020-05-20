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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c577ed76bcf0e998e63421febadf1c01c13e07cb
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831837"
---
# <a name="sp_addmergealternatepublisher-transact-sql"></a>sp_addmergealternatepublisher (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ajoute la possibilité pour un Abonné d'utiliser un partenaire de synchronisation alternatif. Les propriétés de publication doivent spécifier que les Abonnés peuvent opérer des synchronisations avec d'autres serveurs de publication. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données de publication. *publisher_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @alternate_publisher = ] 'alternate_synchronization_partner'`Nom du serveur de publication de remplacement. *alternate_synchronization_partner* est de **type sysname**, sans valeur par défaut.  
  
`[ @alternate_publisher_db = ] 'alternate_publisher_db'`Nom de la base de données de publication sur le serveur de publication de remplacement. *alternate_publisher_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @alternate_publication = ] 'alternate_synchronization_partner'`Nom de la publication sur le partenaire de synchronisation de substitution. *alternate_synchronization_partner* est de **type sysname**, sans valeur par défaut.  
  
`[ @alternate_distributor = ] 'alternate_distributor'`Nom du serveur de distribution pour le partenaire de synchronisation de substitution. *alternate_distributor* est de **type sysname**, sans valeur par défaut.  
  
`[ @friendly_name = ] 'friendly_name'`Nom complet permettant d’identifier l’Association du serveur de publication, de la publication et du serveur de distribution qui constitue un autre partenaire de synchronisation. *friendly_name* est de type **nvarchar (255)**, avec NULL comme valeur par défaut.  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addmergealternatepublisher** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_addmergealternatepublisher**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_dropmergealternatepublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergealternatepublisher-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
